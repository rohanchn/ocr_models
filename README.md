# Layout Models

| model name | training method | parameters | comments |
|----------|----------|----------| ----------|
|urSEG_openiti_PRE_print|finetuned from pretrian_print_layout (openiti)|default with `-N 50`, `--pad 2 2`, and `-bl`|best model; handles multicolumn; baselines need work, especially for slanted lines; need more examples of layouts with `MainZone` and `MarginTextZone` + texts blocks enclosed within boxes within borders| 
|urSEG_regions_openiti_PRE_print|finetuned from pretrain_print_layout (openiti)|default with `-N 50` and `--suppress-baselines`|region only; handles multicolumn; often merges `MarginTextZone` with `MainZone`, especially where separation between `MarginTextZone` and `MainZone` is not clear|
|urSEG_mellon_print|finetuned from mellon_print_layout|default with `-N 50`, `--pad 2 2`, and `-bl`|less certain on pages with both `MaineZone` and `MarginTextZone`|
|urSEG_existing_best_ur_print|finetuned on an existing baseline only model, which was trained from scratch|default with `-N50`, `--pad 2 2 `, and `-bl`|pretty similar to `urSEG_mellon_print` with slightly better baselines|
|urSEG_baselines_existing_best_ur_print|finetuned on an existing baseline only model, which was trained from scratch|default with `-N50`, `--pad 2 2`, and `-bl`|currently training|
|yolov5|trained with <a href="https://github.com/PonteIneptique/YALTAi" target="_blank">YALTAi</a>||weights too large to upload here|

# Trainig Types
|line types|count|
|----------|----------|
|DefaultLine|50620|
|HeadingLine:title|230
|default|178|
|CustomLine:signature|53|

|region Types|count|
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
|text|13|
