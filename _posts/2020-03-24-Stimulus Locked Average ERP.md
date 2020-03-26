---
layout: post
title: Stimulus-Locked ERP Simulation Code
---

This simulation code adds 0.5 microvolts to the 300 - 500 ms window for each 0.1 increase in effect size.

---
```matlab

%Control condition = 1
%Experimental condition = 2

%Call the eeglab function to open it at the start. Datasets are loaded
%through eeglab.
eeglab


%====================================%
%SETTING UP PATHS
%====================================%
%Setting the import and export paths
import_path = ('C:\Users\rjobrien\Desktop\Personal Projects\Thesis Data');

export_path = ('C:\Users\rjobrien\Desktop\Personal Projects\Thesis Data\avg output1');

%Listing all of the files in the folder
filelist = dir(fullfile(import_path, '*.set'));


%====================================%
%PARAMETERS
%====================================%
sample_sizes = {50};    %Sample sizes range from 10 to 50 by 10

effect_sizes = {0, 0.1};                     %Effect sizes range from 0 to 0.5 by 0.1

simulations = 1:500;                    %Running tests with 500 simulations

participants = 1:20;                    %Using 20 participants based on literature

%====================================%
%INITIATING VARIABLES
%====================================%
%Making an empty variable to place all of the individual datasets into
combined_data = [];

%Making an empty variable to place all of the avg datasets into
combined_avg_data = [];


%====================================%
%RANDOMLY SELECTING FILES
%====================================%
%Only a few files are randomly selected from the files list because
%otherwise the population dataset would become too large and the results
%would be uninterpretable.
temp_files = randperm(size(filelist, 1), 8);        %TESTING different sized population datasets (e.g., 1000 - 2500 individual trials)


%====================================%
%LOADING IN THE INDIVIDUAL DATASETS
%====================================%
% for f = 1:length(filelist)
for f = temp_files

   
    %Load each preprocessed/ICA dataset
    try
    EEG = pop_loadset(strcat(import_path, '\', filelist(f).name));
    catch
        "missing file";
    end


    %Combining data together into one large array
    combined_data = cat(3, combined_data, extracting_correct_responses(EEG));
    
end


%Finding the standard deviation of the PZ electrode amplitudes
%Need to reshape the 3D array to 1D array
standard_deviation = std(unique(reshape(combined_data(29,:,:), [], 1), 'rows'));


%====================================%
%CALLING THE SIMULATION FUNCTION AND EXPORTING THE FINAL DATA
%====================================%
for s = 1:length(simulations)
    
    for e = 1:length(effect_sizes)

        for n = 1:length(sample_sizes)

            for p = 1:length(participants)
                
                trials = sample_sizes{n};
                effect_size = effect_sizes{e};
                simulation_num = simulations(s);
                participants_num = participants(p);

                final_data = run_sim(combined_data, simulation_num, effect_size, trials, participants_num);

                %Exporting the final dataset
                csvwrite(strcat(export_path, '\', num2str(simulations(s)), '_', num2str(effect_sizes{e}), '_', num2str(sample_sizes{n}), '_', num2str(participants(p)), '_stimulus_locked_avg_data.csv'), final_data);

            end
        end
    end
end

%Plotting the average waveforms
% plot(squeeze(combined_avg_data(250:400, 29, :)));





%====================================%
%FUNCTIONS
%====================================%

%====================================%
%EXTRACTING THE CORRECT RESPONSES FROM THE EEG DATA
%====================================%
function a = extracting_correct_responses(data)

    %To add even more randomness to the data I made it so that random
    %groups of correct responses would be selected out. This allows for
    %more files to be included.
    flanker_event_type = [1,4,5];
    temp = flanker_event_type(randi(length(flanker_event_type)));

    %subset out all of the EEG event numbered 1, 4, and 5
%     a = data.event(([data.event.type] == 1 | [data.event.type] == 4 | [data.event.type] == 5) & [data.event.response_status] == 2);

    a = data.event(([data.event.type] == temp) & [data.event.response_status] == 2);

    a = struct2cell(a);

    a = squeeze(a)';

    %Subsetting out a vector of epochs           
    epochs = num2cell(unique(cell2mat(a(:, 12))));

    %Subsetting the data based on the correct responses
    a = data.data(:,:, cell2mat(epochs));

end




%====================================%
%RUNNING THE MONTE-CARLO SIMULATION
%====================================%
function b = run_sim(data, simulation_num, effect_size, trials, participants_num)

    combined_avg_data = [];

    %====================================%
    %RESAMPLING WITHOUT REPLACEMENT FROM THE POPULATION DATASET
    %====================================%
%     standard_deviation = std(unique(reshape(data(29,:,:), [], 1), 'rows'));     %USE THIS IF YOU WANT THE STANDARD DEVIATION TO BE PULLED FROM THE POPULATION DATASET
    standard_deviation = 5;

    %Randomly select n * 2 number of trials
    sample_first = randperm(size(data, 3), trials*2);

    %Finding n trials indices to subset from the first sample
    sample_second = randperm(length(sample_first), trials);

    %Subsetting out the second samples values
    sample_three = sample_first(:, sample_second);

    %Removing the second samples values from the first sample
    sample_first(sample_second) = [];


    %====================================%
    %GENERATING THE CONTROL AND EXPERIMENTAL CONDITIONS
    %====================================%
    control_condition = data(:,:, sample_first);

    %I think I need to sample from the combined data again*
    % experimental_condition = combined_data(:,:, s3); 
    experimental_condition = data(:,:, sample_second);


    %====================================%
    %ADDING EFFECT SIZES TO SINGLE TRIALS IN THE EXPERIMENTAL CONDITIONS
    %====================================%
    %Plotting the before and after of the effect size manipulation
%      plot(experimental_condition(29, 250:400, 1));
%      hold on;

    %Adding the effect size voltage to the 300ms - 500ms window of each
    %trial
    %Use the population standard deviation and multiply it by the
    %effect size
    experimental_condition(:, 325:375, :) = experimental_condition(:, 325:375, :) + (standard_deviation * effect_size);

%    plot(experimental_condition(29, 250:400, 1));


    %====================================%
    %CALCULATING THE STIMULUS-LOCKED AVERAGE ERP WAVEFORM
    %====================================%
    %Calculating the average ERPs across trials
    control_condition_mean = mean(control_condition,3);

    %Making the electrodes the columns
    control_condition_mean = permute(control_condition_mean,[2 1]);

    %Adding sample size as a column
    control_condition_mean(:, 35) = trials;

    %Adding effect size as a column
    control_condition_mean(:, 36) = effect_size;

    %Adding condition as a column
    control_condition_mean(:, 37) = 1;

    %Adding simulation number as a column
    control_condition_mean(:, 38) = simulation_num;

    %Adding participant number as a column
    control_condition_mean(:, 39) = participants_num;

    %Calculating the average ERPs across trials
    experimental_condition_mean = mean(experimental_condition,3);

    %Making the electrodes the columns
    experimental_condition_mean = permute(experimental_condition_mean,[2 1]);

    %Adding sample size as a column
    experimental_condition_mean(:, 35) = trials;

    %Adding effect size as a column
    experimental_condition_mean(:, 36) = effect_size;

    %Adding condition as a column
    experimental_condition_mean(:, 37) = 2;

    %Adding simulation number as a column
    experimental_condition_mean(:, 38) = simulation_num;  

    %Adding participant number as a column
    experimental_condition_mean(:, 39) = participants_num;

    %====================================%
    %COMBINING ALL AVERAGE EXPERIMENTAL AND CONTROL CONDITION DATASETS
    %====================================%
    %Combining data together into one large array
    b = cat(3, combined_avg_data, control_condition_mean, experimental_condition_mean);


    %====================================%
    %PLOTTING THE STIMULUS-LOCKED AVERAGE ERP WAVEFORMS
    %====================================%
    %Visually depict 0 - 600 ms to see if there could be latency differences in
    %the P3
%     plot(experimental_condition_mean(250:400, 29));
%     hold on;
%     plot(control_condition_mean(250:400, 29));


    %I subset the data between 250:400 because I know that represents 0 -
    %600 ms
    %Reshaping the data into a long format so that I can work with it in R
    b = reshape(permute(b(250:400, [29, 35:39], :),[2 1 3]), size(b(250:400, [29, 35:39], :),2),[])';

    

end

```
