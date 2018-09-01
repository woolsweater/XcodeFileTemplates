Basic file templates that eschew the boilerplate in the Apple-provided ones.

Installing them is simple:

- Create a directory `~/Library/Developer/Xcode/Templates/File Templates` (it may already exist). Xcode looks in here when you create a new file.
- Clone the repo into there. You probably want to rename the cloned directory; Xcode uses the name as the group header in the file creation sheet.
- There's no step 3

(Unfortunately it seems they will always be at the bottom of the sheet.)

The templates are contained in a bundle structure: each .xctemplate directory has an Info.plist describing its contents, icons for the sheet, and the templates themselves. The Info.plist can describe various options for the template; it's sort of a mini-nib. See https://www.bobmccune.com/2012/03/04/creating-custom-xcode-4-file-templates/ for lots of details.

The options are used to select the template file, whose name is given under the MainTemplateFiles key in the plist (the usual name is just `___FILEBASENAME___`). There's some undocumented process to select the inner directory holding the final template (it seems to be concatenation of the option values). In the Cocoa Touch Class template bundle, for example, you can see subdirectories that each contain a `___FILEBASENAME___` for their respective language.

The templates themselves are basically normal code files, with some placeholders for string substitution when they're instantiated. The known placeholders are listed by Bob Mccune at the above link. Option values that were declared in the Info.plist are available, using `___VARIABLE_myVariableName___` as a placeholder.
