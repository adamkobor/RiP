# RiP

RiP (Replace in Place) is a Quick Action for MacOS, and provides a very basic "Search and Replace" functionality to every application that doesn't have this feature out of the box (which is especially true for **Evernote**).

## How to install?

1. Download *RiP.workflow.zip*, and unzip it
2. Double click and install RiP.workflow
3. (Optional) Add it to your touchbar's quick actions, to be able to use it quickly

## How to use?

Select the text you want to search in, and start the action by choosing it in your Mac's touchbar, or from the context menu (*Services* -> *RiP*)

![Usage]
(https://github.com/adamkobor/RiP/blob/master/rip.gif)

## How does it work?
This is a quite basic Automator workflow, which is basically just a wrapper around the standard `sed` command:

```bash
echo $1 | sed -E 's/'"$2"'/'"$3"'/g'
```

**Where**:
- `$1` is the selected text
- `$2` is the text or **regular expression** you want to search for
- `$3` is the text or **regular expression** you want to replace by

You can use **matcher groups** as well (see examples below).

## Examples

**Input**
```
This is just an example text with numbers (123.45, 60000, 111111).
```

**Find & Replace arguments**

- Find: `text`, Replace: `sentence` -> `This is just an example sentence with numbers (123.45, 60000, 111111).`
- Find: `([0-9]+)\.([0-9]+)`, Replace: `\1|\2` -> `This is just an example text with numbers (123|45, 60000, 111111).`
