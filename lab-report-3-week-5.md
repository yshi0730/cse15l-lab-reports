# Three More Commands for grep 
## grep -l
* This command shows the names of files containing the specific pattern. This can be useful when we know a line of text but don't know which file it comes from. Then we can use this command to find the specific files.
* Also note that replacing -l with -L shows names of files not containing the specific pattern.
* Example 1 : Search for files containing the word "Tuesday" in the 911report folder.
```
sys@Syss-Air 911report % grep -l "Tuesday" *    
chapter-1.txt
chapter-13.2.txt
chapter-13.4.txt
```
* Example 2 : Search for files containing the word "America" in the Alcohol_Problems folder.
```
sys@Syss-Air Alcohol_Problems % grep -l "America" * 
Session2-PDF.txt
Session3-PDF.txt
Session4-PDF.txt
```
* Example 3 : Search for files containing the word "Biology" in the biomed folder.
```
sys@Syss-Air biomed % grep -l "Biology" *
1471-2156-2-17.txt
1471-2164-2-8.txt
1471-2164-3-32.txt
1471-2164-3-6.txt
1471-2164-4-15.txt
1471-2164-4-21.txt
1471-2180-1-26.txt
1471-2180-1-33.txt
1476-4598-2-1.txt
1477-7827-1-13.txt
1477-7827-1-46.txt
gb-2001-2-4-research0012.txt
gb-2003-4-2-r16.txt
```
## grep -h
* This command shows the lines containing the specific pattern. This is useful when we wants to look up a keyword and search for paragraph/lines about that keyword. 
* Example 1 : Search for lines containing the word "excessive" in the Alcohol_Problems folder.
```
sys@Syss-Air Alcohol_Problems % grep -h "excessive" *
The problem is the consequences resulting from excessive
A. Screening for excessive alcohol drinking: comparative value of
and patient plans to address excessive drinking. Prototypic
for excessive drinkers: the need for caution. Alcohol Alcohol
excessively. Second, the ED is a fast-paced environment in which
```
* Example 2 : Search for lines containing the phrase "carbon dioxide" in the Env_Prot_Agen folder.
```
sys@Syss-Air Env_Prot_Agen % grep -h "carbon dioxide" *
title IV of the Clean Air Act shall also monitor carbon dioxide
mercury (Hg), and carbon dioxide (CO2) emissions from the US
Reduce carbon dioxide (CO2) emissions to 1990
sulfur dioxide (SO2), and carbon dioxide (CO2). Although a
air pollutants and carbon dioxide (CO2) emissions. The study,
of carbon dioxide from electric power generators. The legislation
Amendments of 1990 to retain the existing carbon dioxide monitoring
```
* Example 3 : Search for lines containing the word "casualties" in the 911 report folder.
```
sys@Syss-Air 911report % grep -h "casualties" *
                casualties and whether, by sharing intelligence with Massoud on Bin Ladin's possible
                central Baghdad. The attack was made at night, to minimize civilian casualties.
                casualties-"collateral damage"-was too high. They were concerned about the tribals'
                "Hiroshima"and at least 10,000 casualties. The CIA reported RESPONSES TO AL QAEDA'S
                Clarke told us the threat was seen as one that could cause hundreds of casualties,
                to 11 families in the Tarnak Farms facility, which could mean 60-65 casualties.
                rather than to inflict mass casualties. The study is said to have considered the
                over Lockerbie, Scotland- a promising means to inflict massive casualties; and (3)
                the big attack, with lots of casualties, after which some major US retaliation will
                near-term "spectacular" terrorist attacks resulting in numerous casualties. Other
```
## grep -i
* This command searches for lines containing the specific pattern regardeless of upper/lower case. (-i for ignore) This is useful because sometimes we can miss important lines of contents because the upper/lower case doesn't match.
* Example 1 : It shows the lines with the word "president" even I typed "PresIDEnt".
```
sys@Syss-Air 911report % grep -i "PresIDEnt" chapter-2.txt
                (such as those promoted by Egyptian President Gamal Abdel Nasser's Arab Socialism or
                President Anwar Sadat in 1981, the Egyptian government combined harsh repression of
                President Bush observed." Islam is a faith that brings comfort to a billion people
                movement-badly battered in the government crackdown following President Sadat's
                General Omar al Bashir, president since 1989, had never been entirely under his
            The attempted assassination in Ethiopia of Egyptian President Hosni Mubarak in June
```
* Example 2 : It shows the lines with the word "terrorism" even if I typed "terroRISM".
```
sys@Syss-Air 911report % grep -i "terroRISM" chapter-5.txt
            Al Qaeda's success in fostering terrorism in Southeast Asia stems largely from its
```
* Example 3 : It shows the liens with the phrase "weight loss" even though I typed the phrase all capitalized.
```
sys@Syss-Air biomed % grep -i "WEIGHT LOSS" 1468-6708-3-1.txt
          pounds or more unintended weight loss in the year before
        unintended weight loss. Among blacks, gender differences
        loss and weight loss since age 50. Among males, there were
        unintended weight loss, YOL, YHL, years of unhealthy life,
        significantly on BMI, BMI>30, weight loss since age 50,
        in weight loss since age 50 was no longer significant.
          outcome for a trial of weight loss in older adults
```
