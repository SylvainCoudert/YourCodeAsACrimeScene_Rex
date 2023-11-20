# YourCodeAsACrimeScene_Rex

Vous trouverez ici la plupart des ressources concernant mon talk *"Code case: les méthodes de la crim adaptées au code".*

D'une manière général, Adam Tornhill recence ici tous les outils nécessaires à la mise en place de ce qu'il conseille à cette adresse : [https://www.adamtornhill.com/code/crimescenetools.htm](https://www.adamtornhill.com/code/crimescenetools.htm)

Durant mon talk, j'utilise Code Maat trouvable ici :  \
[https://github.com/adamtornhill/code-maat](https://github.com/adamtornhill/code-maat) pour analyser les logs git. \
J'utilise également Cloc pour les calculs de complexité : \
[https://github.com/AlDanial/cloc](https://github.com/AlDanial/cloc). \
Pour les scripts Python fournis par Adam Tornhill, j'utilise les versions corrigées et remises en conformité avec Python 3 par Romain Berthon :  \
[https://github.com/RomainTrm/YourCodeAsACrimeSceneExercices/tree/main/scripts](https://github.com/RomainTrm/YourCodeAsACrimeSceneExercices/tree/main/scripts) \
Par ailleurs, Adam Tornhill a également proposé une mise à jour des mêmes scripts sur son propre Github : \
[https://github.com/adamtornhill/maat-scripts/tree/python3](https://github.com/adamtornhill/maat-scripts/tree/python3)

Les différentes sont directement copiées ou très fortement inspirées de ce qu'on trouve dans le livre mais les voici dans l'ordre d'apparition: \
git log --pretty=format:'[%h] %an %ad %s' --date=short --numstat --after=2022-01-10 --before=2023-30-09 > maat_evo.log \
java -jar code-maat-1.0.4-standalone.jar -c git -l maat_evo.log -a summary \
java -jar code-maat-1.0.4-standalone.jar -c git -l maat_evo.log -a revisions > maat_freqs.csv \
.\cloc ./{MyLocalFolder} --by-file --csv --quiet --report-file=maat_lines.csv

**WARNING** \
Sous Windows, cloc va utiliser les backslash comme séparateur dans les chemins, incompatibles avec 
les analyses suivantes!

python ./scripts/merge_comp_freqs.py maat_freqs.csv maat_lines.csv \
python ./scripts/csv_as_enclosure_json.py --structure maat_lines.csv --weights maat_freqs.csv --weightcolumn 1 > report.json

python ./scripts/git_complexity_trend.py --start {StartCommit} --end {EndCommit} --file {FileName} > {fileNameexport.csv}

java -jar code-maat-1.0.4-standalone.jar -c git -l maat_evo.log -a coupling > coupling.csv


**Remerciements spéciaux** pour *Adam Tornhill* et son livre *"Your code as a crime scene"*, et à *Romain Berthon* et *Adrien Turpin* sans qui je n'aurais pas encore croisé la route de cet ouvrage!
