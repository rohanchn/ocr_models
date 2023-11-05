# Layout Models

|model name|training method|parameters|comments|
|----------|----------|----------|----------|
|urSEG_baselines_only|finetuned on an existing baseline only model, which was trained from scratch|`--suppress-regions`, `--epochs 50`, `--pad 2 2`, `-bl`, rest default|baseline only; good for `DefaultLine`; needs more examples of `HeadingLine` and `CustomLine:signature`; requires more work for `DefaultLine:prose` and `DefaultLine:verse`|
|urSEG_openiti_PRE_print|finetuned from pretrian_print_layout (openiti)|`--resize both`, `--epochs 50`, `--pad 2 2`,`-bl`, rest default|best model; handles multicolumn (easily confused between multicolumn prose and verse); baselines need work, especially for slanted lines; need more examples of layouts with `MainZone` and `MarginTextZone` + texts blocks enclosed within boxes within borders| 
|urSEG_mellon_print|finetuned from mellon_print_layout (openiti)|`--resize both`, `--epochs 50`, `--pad 2 2`, and `-bl`|poor on pages with both `MaineZone` and `MarginTextZone`; masks from baselines is not ideal|
|urSEG_existing_best_ur_print|finetuned on an existing baseline only model, which was trained from scratch|`--resize both`, `--epochs 100`, `--min-epochs 50`, `--quit early`, `--lrate 0.0001`, and `-bl`, rest default|better regions and baselines on extended classes|
|urSEG_regions_from_scratch|trained from scratch|`--suppress-baselines`, `--epochs 70`, rest default|region only; handles multicolumn upto three columns; prone to merge `MarginTextZone` and `MainZone`, especially where separation between the two is less clear|
|urSEG_regions_openiti_PRE_print|finetuned from pretrain_print_layout (openiti)|`--resize both`, `--suppress-baselines`, `--epochs 70`, rest default|region only; similar to `urSEG_regions_from_scratch`, but worse to finetune|
|yolov5|trained with <a href="https://github.com/PonteIneptique/YALTAi" target="_blank">YALTAi</a>||weights too large to upload here|


# Training Types; 
For the latest `urSEG_existing_best_ur_print.mlmodel`
|line types|count|
|----------|----------|
|DefaultLine|133857|
|HeadingLine:title|1514|
|CustomLine:signature|63|
|HeadingLine:incipit|23
 
|region types|count|
|-------|-------|
|NumberingZone:page|3693|
|RunningTitleZone|3001|
|MainZone|2788|
|MainZone:column#1|1213|
|MainZone:column#2|1207|
|MarginTextZone:note|712|
|CustomZone:publication|620|
|MainZone:column#3|441|
|MarginTextZone:commentary|257|
|DigitizationArtefactZone|247|
|QuireMarksZone:catchwords|160|
|TitlePageZone|71|
|MarginTextZone:note#2|59|
|MarginTextZone:note#1|52|
|GraphicZone:illustration|17|
|NumberingZone:other|9|

Trained with [Kraken](https://github.com/mittagessen/kraken) `==4.3.13`
