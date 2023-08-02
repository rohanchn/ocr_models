# Layout Models

|model name|training method|parameters|comments|
|----------|----------|----------|----------|
|urSEG_baselines_only|finetuned on an existing baseline only model, which was trained from scratch|`--suppress-baselines`, `--epochs 50`, `--pad 2 2`, `-bl`, rest default|baseline only; good for DefaultLine; needs more examples of HeadingLine and CustomLine:signature; requires more work for DefaultLine:prose and DefaultLine:verse|
|urSEG_openiti_PRE_print|finetuned from pretrian_print_layout (openiti)|`--resize both`, `--epochs 50`, `--pad 2 2`,`-bl`, rest default|best model; handles multicolumn (easily confused between multicolumn prose and verse); baselines need work, especially for slanted lines; need more examples of layouts with `MainZone` and `MarginTextZone` + texts blocks enclosed within boxes within borders| 
|urSEG_mellon_print|finetuned from mellon_print_layout|`--resize both`, `--epochs 50`, `--pad 2 2`, and `-bl`|poor on pages with both `MaineZone` and `MarginTextZone`; masks from baselines is not ideal|
|urSEG_existing_best_ur_print|finetuned on an existing baseline only model, which was trained from scratch|`--resize both`, `--epochs 50`, `--pad 2 2 `, and `-bl`, rest default|pretty similar to `urSEG_mellon_print` for regions; better baselines|
|urSEG_regions_from_scratch|trained from scratch|`--suppress-baselines`, `--epochs 70`, rest default|region only; handles multicolumn upto three columns; prone to merge `MarginTextZone` and `MainZone`, especially where separation between the two is less clear|
|urSEG_regions_openiti_PRE_print|finetuned from pretrain_print_layout (openiti)|`--resize both`, `--suppress-baselines`, `--epochs 70`, rest default|region only; similar to urSEG_regions_from_scratch, except worse to finetune|
|yolov5|trained with <a href="https://github.com/PonteIneptique/YALTAi" target="_blank">YALTAi</a>||weights too large to upload here|


# Trainig Types
|line types|count|
|----------|----------|
|DefaultLine|50620|
|HeadingLine:title|230
|CustomLine:signature|53|

|region types|count|
|----------|----------|
|NumberingZone:page|1764|
|MainZone|1305|
|RunningTitleZone|1458|
|MainZone:column#1|556|
|MainZone:column#2|548|
|MarginTextZone:note|327|
|CustomZone:publication|172|
|MarginTextZone:note#2|58|
|MarginTextZone:note#1|47|
|TitlePageZone|41|
|QuireMarksZone:catchwords|26|
|DigitizationArtefactZone|8|
|GraphicZone:illustration|5|
|NumberingZone:other|3|
|GraphicZone:ornamentation|2|

# Types for region only models
|region types|count|
|-------|-------|
|NumberingZone:page|2377|
|RunningTitleZone|2337|
|MainZone|1669|
|MainZone:column#2|870|
|MainZone:column#1|869|
|MarginTextZone:note|587|
|MarginTextZone:commentary|220|
|MainZone:column#3|202|
|CustomZone:publication|173|
|MarginTextZone:note#2|68|
|MarginTextZone:note#1|55|
|TitlePageZone|43|
