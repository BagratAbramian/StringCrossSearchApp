StringCrossSearchApp v 1.1

Developed by Bagrat Abramian Petrosian, using MATLAB R2019b

Special thanks to:
David Abramian (https://github.com/DavidAbramian), for providing the main function around which this entire app operates.
Roman Ramirez (https://github.com/patowc), for suggesting I develop the above-mentioned function into an app.
All the people who ask and answer in MATLAB Answers (https://www.mathworks.com/matlabcentral/answers/).

This is a basic application developed for the purpose of comparing string arrays.
In particular, this is an app developed for searching many different substrings within strings.

This file is to explain the meaning of the various functions this app possesses, as well as to try to explain any possible problems.

1. Inputs and UI

The UI is divided in 2 tabs, "Basic Options" and "Advanced Options"

1.1 Basic Options

1.1.1 Detect/correct special characters in input files

This option allows the program to check when importing the data vector, search vector, data tags, or search tags, whether or not they contain special characters which may have been imported incorrectly.
If detected, a prompt will appear asking what to do with the input file:
	Keep: It doesn't change anything, as if the "Detect/correct special characters in input files" hadn't been selected.
		 This is the default option;
	Discard: It discards the vector or tags file;
	Correct: The program will attempt to correct the file to restore it to the intended state.
		 Depending on the options selected in "Special characters' correction options" (see 1.2.1), it will attempt to correct those types of characters.
		 This process may become time-consuming depending on the number of entries in the file to correct and the correction options selected.

1.1.2 Import data vector

Imports the data in which you want to search the various substrings.
The source file must be in the form of a vertical vector.

1.1.3 Import search vector

Imports the list of substrings to be searched in the data vector.
The source file must be in the form of a vertical vector.

1.1.4 Check search vector conflicts

Searches whether any of the substrings of the search vector is also a substring of any other substring.
The resulting conflict report is printed in the "Search vector conflicts" text box (see 1.1.5).

1.1.5 Search vector conflicts

Lists the results of the "Check search vector conflicts" operation.

1.1.6 Import data tags

Imports a file to serve as tags for each of the entries of the data vector.
The data tags do not affect the search, but are printed when exporting as "Export combined data matrix with totals" and "Full matrix".
The data tags file must have the same number of rows as the data vector, and must be a vertical vector itself.

1.1.7 Clear data tags

Removes the current data tags loaded, so as to keep it from appearing in the export files.

1.1.8 Import search tags

Imports a file to serve as tags for each of the entries of the search vector.
The data tags do not affect the search, but are printed when exporting as "Export combined search matrix with totals" and "Full matrix".
The search tags file must have the same number of rows as the search vector, and must be a vertical vector itself.

1.1.9 Clear data tags

Removes the current search tags loaded, so as to keep it from appearing in the export files.

1.1.10 Export total search values vector (per data point)

Upon run, creates a text file with a vertical vector for the number of substrings found in each string.
The name of the file is defined in the "Total search values vector (pdp) filename" textbox.
The folder in which it will be created is defined with the "Select output folder" button.

1.1.11 Export total search values vector (per search point)

Upon run, creates a text file with a vertical vector for the number of strings in which the respective substring is found.
The name of the file is defined in the "Total search values vector (psp) filename" textbox.
The folder in which it will be created is defined with the "Select output folder" button.

1.1.12 Export combined data matrix with totals

Upon run, creates a xls file with the first column being the data vector, and the second will be the number of substrings found in each string.
If there are data tags, the first column will be the data tags, the second will be the data vector, and the third will be the number of substrings found in each string.
The name of the file is defined in the "Combined data matrix filename" textbox.
The folder in which it will be created is defined with the "Select output folder" button.

1.1.13 Export combined search matrix with totals

Upon run, creates a xls file with the first column being the search vector, and the second will be the number of strings in which the respective substring is found.
If there are search tags, the first column will be the search tags, the second will be the search vector, and the second will be the number of strings in which the respective substring is found.
The name of the file is defined in the "Combined search matrix filename" textbox.
The folder in which it will be created is defined with the "Select output folder" button.

1.1.14 Help

Opens the "help.txt" file (The file you are reading right now).

1.1.15 Normalize vectors

Normalizes the data and search vectors according to the "Normalization options" selected (see 1.2.4).
This button doesn't perform any changes on the data and search tags, thus the same file used for data and search vectors may be imported as their own respective tags in order to preserve their state pre-normalization.

1.1.16 Select output folder

Designates the folder in which the output file(s) will be saved.

1.1.17 Run cross-search

Executes the cross-search of the search vector in the data vector, and generates all the output files chosen.

1.1.18 Current file names

These text boxes display the currently loaded files' names.

1.1.19 Current output directory

This text box displays the direction where the output files will be created.

1.2 Advanced Options

1.2.1 Special characters' correlation options

Selects which types of characters will be corrected if special characters are detected and "Correct" is selected (see 1.1.1).
By default, "General symbols" and "Latin characters" are checked, while "Greek characters" and "Cyrilic characters" are unchecked.
The more options selected, the longer the correction will take.
To see which characters are in each group, as well as which symbols cause no trouble, see 4.1.

1.2.2 Export verification matrix (not recomended)

Upon run, creates a text file with the comma-separated correlation matrix which describes precisely which substrings are found in each string.
The name of the file is defined in the "Verification matrix filename" textbox.
The folder in which it will be created is defined with the "Select output folder" button.
(!) Checking this option is not recommended, as it can create very large files for even medium-sized data and search vectors.
(e.g. A data vector of 15595 entries with a search vector of 2692 created a .txt file of over 82000 KB).

1.2.3 Export full matrix (not recomended)

Upon run, creates a xls file with 2 sheets.
In the sheet "data_x_search" the first column being the data vector, the second to the penultimate columns are whether the respective search entry appears in each entry of the data vector, 
and the last row is a sum of all the search entries that appear in the corresponding data entry.
The first row is the search vector, the second to penultimate rows are whether or not the respective data entry contains the each search entry, 
and the last column is a sum of all the data entries that contain in the corresponding search entry.
If there are data and/or search tags, they will instead take the first column and row respectively, displacing everything else one position.
The sheet "search_x_data" is the sheet "data_x_search" transposed.
The name of the file is defined in the "Full matrix filename" textbox.
The folder in which it will be created is defined with the "Select output folder" button.
(!) Checking this option is HIGHLY not recomended, as it can take a lot of memory, time, and computational power to export even for the smallest of matrices.
(e.g. The dataset mentioned in the example on 1.2.2 caused the program to crash).

1.2.4 Normalization options

Selects which type of normalization will be performed when using "Normalize vectors" (see 1.1.4).
By default, Lowercase vectors" is checked, while "Normalize diacritics" is unchecked.
"Lowercase vectors" puts all the characters of a vector in lowercase, to avoid having to duplicate the search vector with both capitalized and uncapitalized versions of each entry.
However, if capitalization is key to your cross-search, uncheck this option.
"Normalize diacritics" changes various letters with diacritics into the same letters without them.
Note that this isn't done with German in mind, thus Ä, Ö, and Ü (and their lowercase equivalents) are normalized as "A", "O", and "U", rather than "AE", "OE" and "UE".
To see which characters with diacritics are changed, see 4.2.

2 Errors and Warnings

2.1 The [import] must be a vertical vector.

If trying to import a file with that isn't a vertical vector, this error message will appear.
Please make sure that your input only contains one column.
Most .txt files, even those with commas, semicolons, apostrophes, and quotation marks should work as data vectors, although there are some exceptions.

2.2 No [type] vector imported.

If trying to perform an action which requires a vector without having imported one, theis error message will appear.
Please make sure that you have imported a data vector before trying to operate with it.

2.3 You have not selected any output.

If trying to run a cross-search when there are no export checkboxes checked, this error message will appear.
Since the "Run cross-search" function's only purporse is to create files of the results of the cross-search, running it without exporting any of the results would only consume resources.
Please select at least one of the export options before trying to execute a cross-search.

2.4 Two or more output files have the same name. (This message will appear regardless of whether or not the conflicting outputs have both been selected).

If trying to use "Run cross-search" when two or more of the output file names are identical, this error message will appear.
As the message indicates, this will happen even if the export file in conflict is not selected.
Please assign non-conflicting names to the various export files.

2.5 No output folder specified.

If trying to use "Run cross-search" before specifying an output folder, this error message will appear.
Please specify an output folder before running a cross-search.

2.6 No name given to output file.

If trying to use "Run a cross-search" when any of the selected output files has been left with a blank name, this error will appear.
Please assing a name to the output files before running a cross-search.

2.7 The [import] has not been imported as a cell or string array.

If the imported file has not been imported as a cell or string array, this error message will appear.
Please check that your imput file doesn't follow some structure which may make it be interpreted as a numbered array or some other kind of data structure.
e.g. You may have to add a text line in the end if alll your input data consists of numbers simply to ensure the program identifies it as a string or cell.

2.8 To apply [type] tags you have to first import a [type] vector.

If trying to import tags before the corresponding vector has been imported, this error will appear.
Since the tags file has to be the same length as its corresponding vector, you need to import the vector first.

2.9 The [type] tags file has to be the same length as the [type] vector.

If trying to import a tags file with a different number of rows than the corresponding vector, this error will appear.
Keep in mind some of the possible import issues that may lead to this error showing even if both files have the same number of rows in the original file (see 3.1).

2.10 No special characters' type correction chosen. [Import] imported as-is.

If special characters are detected in your import file and you choose "Correct", but have no "Special characters' correction options" checked, this warning will appear.

2.11 The previous [type] tags length doesn't match the new [type] vector, and thus has been removed.

If you import a new vector after having imported a corresponding tags file, and the number of rows of the new vector doesn't match that of the tags file, this warning will appear.
The tags file will be automatically discarded.

2.12 There is a [type] tags file loaded of the same length as the new [type] vector. Do you want to keep it?

If you import a new vector after having imported a corresponding tags file, and the number of rows of the new vector matches that of the tags file, this question will appear.
	Yes: The tags file is kept.
		 This is the default option;
	No: The tags file is discarded.

2.13 The product of the lengths of your vectors exceeds 10 million. The generation of a full matrix is a very memory-intensive process, and it may fail or carsh the program. Are you sure you want to try and export a full matrix?

It the number of rows of your data vector multiplied by the number of rows of your search vector exceeds 10 million, this warning will appear.
As the creation of the full matrix is very resource- and time-intensive, this warning is your last chance to rethink whether or not you truly want to create one.
	Yes: The program will attempt to create a full matrix;
	No: The program will not attempt to create a full matrix.
		 This is the default option.
Note that if the only export you requested is a full matrix, error 2.3 will appear.

3 Known issues

3.1 Import issues

3.1.1 Empty lines are skipped when importing

e.g. A file with
Hello

friend
will be imported as
Hello
friend

3.1.2 Lines which contain only a space stop the import from proceding further in the file

e.g. A file with
Hello
 
friend
will be imported as
Hello

3.2 Normalization issues

3.2.1 If your vectors have special characters that have not been corrected, using "Lowercase vectors" may lead to misidentifications during the cross-search.

e.g. Ê (ÃŠ) and Ú (Ãš) will be rendered identical. Same with Ì (ÃŒ) and Ü (Ãœ).

3.2.2 If your vectors have special characters that have not been corrected, using "Normalize diacritics" may lead to misidentifications during the cross-search.

e.g. é (Ã©) and © (Â©) will be rendered identical. Same with ã (Ã£) and £ (Â£).

4 Other information

4.1 Symbols and special characters that are detected and normalized

4.1.1 Symbols that do not cause import problems

!	$	+	}
?	%	*	-
|	&	(	_
@	/	)	.
#	=	opening brakets	:
~	^	closing brakets	,
"	`	{	;


4.1.2 General symbols corrected

!	$	+	}
?	%	*	-
|	&	(	_
@	/	)	.
#	=	[	:
~	^	]	,
"	`	{	;

4.1.3 Latin characters corrected

Á	Ô	ä	ô
Ä	Õ	à	õ
À	Ú	â	ú
Â	Ü	ã	ü
Ã	Ù	é	ù
É	Û	ë	û
Ë	Ñ	è	ñ
È	Ç	ê	ç
Ê	Å	í	å
Í	Æ	ï	æ
Ï	Ð	ì	ð
Ì	Ø	î	ø
Î	Ý	ó	ý
Ó	Œ	ö	œ
Ö	á	ò	ß
Ò			

4.1.4 Greek characters corrected

Ά	Κ	έ	ο
·	Λ	ή	π
Έ	Μ	ί	ρ
Ή	Ν	ΰ	ς
Ί	Ξ	α	σ
Ό	Ο	β	τ
Ύ	Π	γ	υ
Ώ	Ρ	δ	φ
ΐ	Σ	ε	χ
Α	Τ	ζ	ψ
Β	Υ	η	ω
Γ	Φ	θ	ϊ
Δ	Χ	ι	ϋ
Ε	Ψ	κ	ό
Ζ	Ω	λ	ύ
Η	Ϊ	μ	ώ
Θ	Ϋ	ν	ϐ
Ι	ά	ξ	ϑ

4.1.5 Cyricic characters corrected

Ё	Й	а	ч
Ђ	К	б	ш
Ѓ	Л	в	щ
Є	М	г	ъ
Ѕ	Н	д	ы
І	О	е	ь
Ї	П	ж	э
Ј	Р	з	ю
Љ	С	и	я
Њ	Т	й	ё
Ћ	У	к	ђ
Ќ	Ф	л	ѓ
Ў	Х	м	є
Џ	Ц	н	ѕ
А	Ч	о	і
Б	Ш	п	ї
В	Щ	р	ј
Г	Ъ	с	љ
Д	Ы	т	њ
Е	Ь	у	ћ
Ж	Э	ф	ќ
З	Ю	х	ў
И	Я	ц	џ

4.2 Diacritics' normalization

original | new	||   original	 | new
----------------------------------------
   Á	 | A	||	á	 | a
   Ä	 | A	||	ä	 | a
   À	 | A	||	à	 | a
   Â	 | A	||	â	 | a
   Ã	 | A	||	ã	 | a
   Å	 | A	||	å	 | a
   É	 | E	||	é	 | e
   Ë	 | E	||	ë	 | e
   È	 | E	||	è	 | e
   Ê	 | E	||	ê	 | e
   Í	 | I	||	í	 | i
   Ï	 | I	||	ï	 | i
   Ì	 | I	||	ì	 | i
   Î	 | I	||	î	 | i
   Ó	 | O	||	ó	 | o
   Ö	 | O	||	ö	 | o
   Ò	 | O	||	ò	 | o
   Ô	 | O	||	ô	 | o
   Õ	 | O	||	õ	 | o
   Ú	 | U	||	ú	 | u
   Ü	 | U	||	ü	 | u
   Ù	 | U	||	ù	 | u
   Û	 | U	||	û	 | u

5 Contact information

To contact the developer, please send an email to bagratap@gmail.com
Or through GitHub at github.com/BagratAbramian
