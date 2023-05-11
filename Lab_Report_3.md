# Lab Report 3
## Researching `grep`
Source: https://www.geeksforgeeks.org/grep-command-in-unixlinux/
## `-C num`
```
$ grep -C3 one cc3.txt 
          
          
            Midazolam
            In one study of ICU patients receiving midazolam,
            alpha frequency decreased and beta activity became
            prominent. In higher doses, these changes disappeared
            to be replaced by delta/theta activity [ 10]. The onset
--
        Potential practical application of bedside
        electroencephalography
        Modern miniaturized electroencephalographic monitors
        (Fig 1) can be positioned at the bedside, visible to the
        clinical team but out of the way of nursing procedures.
        They are attached to the patient's frontal cranium by
        non-invasive patches similar to electrocardiogram (EKG)
--
        they are likely. The risk to the patient from non-invasive
        cerebral functioning is non-existent and the potential
        benefits at least theoretically possible. The relatively
        small purchase price for one monitor spreads out quickly if
        the monitor can be used for numerous patients in an ICU
        setting. It seems likely that the protection and
        preservation of man's most valuable organ is entirely
```
This is an example of using the `-C num` option on grep, which takes a number and a pattern, and returns the line(s) containing the pattern plus the specified number of lines before and after the line(s) found.
This option could be useful if one did not just want to find the line(s) containing a pattern, but context surrounding the lines, perhaps for when searching for a word that has two different connotations.
```
$ grep -C2 two cc343.txt 
        white blood counts (WBCs) ≥ 12000/mm 3or ≤ 4000/mm 3; and
        (4) obvious source of infection. Group 1 (definite sepsis)
        had positive blood cultures and two or more criteria; Group
        2 (probable sepsis) had an obvious source of infection and
        two or more additional criteria; Group 3 (possible sepsis)
        had fever and leukocytosis or leukopenia with no obvious
        source of infection nor positive blood culture; and Group 4
--
        There were no statistically significant differences in
        age, sex, or admission temperature among the different
        groups. Twenty-two patients (Groups 1 and 2) met the
        criteria for the sepsis syndrome [ 1]. The mean SVR was 445
        ± 168 dynes × s/cm 5, CO was 10.86 ± 5.22l/min; and CI was
--
        salicylates with clinical, laboratory, and hemodynamic
        features of sepsis, but without bacteriological evidence.
        In two of the cases, TNF-α, IL-1 and IL-6 were measured and
        found to be significantly elevated. Other drugs have been
        associated with a low SVR including tricyclic
```
This is another example, using a different file and pattern, and finding two surrounding lines of context. Note the first chunk is long as lines 3 and 5 both match the pattern.
Another use for this option could be searching a java class name and then looking in for a commented description or instance variables.
## `-c`
```
$ grep -c one cc3.txt 
3
```
This is an example of using the `-c` option, which counts the number of lines that match the specified pattern.
Given that the pattern and file are the same as a previous command, we can verify that the number of lines matches the number of chunks given by `-C`.
This could be used to see how often a function is called in a java file. 
```
$ grep -c two cc343.txt 
4
```
This is another example of the same option, again repeating a pattern and file combination from earlier. 
This time, 4 is printed even though `-C` gave 3 chunks because the first chunk contained two lines matching the pattern.
## `-w`
```
$ grep -w two cc343.txt 
        had positive blood cultures and two or more criteria; Group
        two or more additional criteria; Group 3 (possible sepsis)
        groups. Twenty-two patients (Groups 1 and 2) met the
        In two of the cases, TNF-α, IL-1 and IL-6 were measured and
```
This is an example of using the `-w` option, which only shows the lines that match the whole word of the pattern, instead of only partially.
Here, all lines found previously match the word given as the pattern exactly (not `...two...` with no spaces around the pattern).
```
$ grep -w one cc3.txt 
            In one study of ICU patients receiving midazolam,
        small purchase price for one monitor spreads out quickly if
```
This is another example of the same option, but this time showing a different number of lines than previously seen. This is because one of the lines was shown becuase it had the word `positioned` which contains the pattern `one`.
This could be useful for precisely the same behavior we have here; to only find the specified word and not, perharps, a compound word containing the desired word.
## `-l`
```
$ grep -l twice cc3.txt cc2171.txt cc105.txt cc103.txt 
cc2171.txt
```
This is an example of using the `-l` option, which shows the files that contain a line that matches the pattern. 
From this result, we can see that only `cc2171.txt` contains the pattern `twice`.
```
$ grep -l once cc3.txt cc2171.txt cc105.txt cc103.txt cc1856.txt cc1843.txt 
cc3.txt
cc105.txt
cc103.txt
cc1856.txt
cc1843.txt
```
Here is another example of the same option, but now showing that only `cc2171.txt` does not contain a line matching the pattern. 
Another potential use for this option is to find which of several java files reference a class defined in another location. 






