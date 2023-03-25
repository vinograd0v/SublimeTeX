# SublimeTeX

This is a LaTeX setup guide for Sublime Text with LaTeXTools. In this repository, you will find solutions to all the problems that usually arise when installing this package, as well as a customization guide.

  ![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Workstation.png)


# Download:

- [Sublime text here.]( https://www.sublimetext.com/)
- [MiKTeX here.](https://miktex.org/download)
- [Sumatra PDF here.](https://www.sumatrapdfreader.org/download-free-pdf-viewer)
- [ImageMagick here.](https://imagemagick.org/script/download.php#windows)


# Install

- Install Sumatra first and then MiKTeX and then ImageMagick. Finally install Sublime Text. Make sure that ImageMagick is added to the Windows Path during installation. The option should be checked during installation. Additionally, SumatraPDF must also be added to the Path. However, you must do this manually by finding the installation folder of SumatraPDF and adding it to the Path.
  
  ![Alt text](/images/Path.png "Path")


# Sublime Configs

- Open the Command Palette : Press `Ctrl+Shift+P`

- Type ‘install’ in the Command Palette input box, which should autocomplete to ‘Install Package Control.’ Press Enter to select it.

- Sublime Text 3 will start installing Package Control. This may take a short while. Once installed, a pop-up will display the message: Package Control was successfully installed.

- Go to `Preferences  → Package Settings  →  Package Control  → Settings` and paste the following

  ```json
  {
	"bootstrapped": true,
	"in_process_packages":
	[
	],
	"installed_packages":
	[
		"A File Icon",
		"Agila Theme",
		"AutoPEP8",
		"ayu",
		"DistractionFreeWindow",
		"Dracula Color Scheme",
		"Fold Comments",
		"gruvbox",
		"ImageMagick",
		"Language - Spanish",
		"LaTeX Word Count",
		"LaTeX-cwl",
		"LaTeXTab",
		"LaTeXTools",
		"LaTeXYZ",
		"Non Text Files",
		"Package Control",
		"Python 3",
		"SideBarEnhancements",
		"Theme - Gravity",
	],
  }
  ```

- Save the file. This will automatically install all the packages necessary for the setup.  Wait for 5-10 mins for the installation to complete.

- Next open `Preferences  → Settings`  and paste the following there.

  ```json
  {
    "auto_complete_triggers":
    [
        {
            "characters": ".",
            "selector": "source.python - string - comment - constant.numeric",
        },
        {
            "characters": "\\",
            "selector": "text.tex.latex",
        }
    ],
    "color_scheme": "Packages/ayu/ayu-dark.sublime-color-scheme",
    "default_line_ending": "unix",
    "font_size": 11,
    "ignored_packages":
    [
        "Vintage",
    ],
    "open_externally_patterns":
    [
        "*.jpg",
        "*.jpeg",
        "*.png",
        "*.gif",
        "*.zip",
        "*.pdf"
    ],
    "rulers":
    [
        100
    ],
    "tab_size": 4,
    "theme": "ayu-dark.sublime-theme",
    "translate_tabs_to_spaces": true
  }
  ```

- Go to `Preferences→Key Bindings` and paste the following 

  ```json
  [
      { "keys": ["f1"], "command": "toggle_side_bar" },
      { "keys": ["f2"], "command": "distraction_free_window" },
      { "keys": ["f3"], "command": "fold" },
      { "keys": ["f4"], "command": "unfold" },
  ]
  ```

- Now finally go to `Preferences→Package settings→Latex tools→Check system` to check whether everything is fine or not.

# Dark Mode

In Sumatra PDF go to `Settings→Advanced Options`. The settings will open in a new text document. Change the `MainWindowBackground = #11141b` and replace the code in `FixedPageUI` with the following

```
FixedPageUI [
	# Light Mode
	# TextColor = #000000
	# BackgroundColor = #ffffff

	# Dark Mode
	TextColor = #ffffff
	BackgroundColor = #11141b
	SelectionColor = #f5fc0c
	WindowMargin = 2 4 2 4
	PageSpacing = 4 4
]
```

This will activate dark mode in Sumatra. To revert back to light mode just un-comment the lines under `Light Mode` and comment the lines under `Dark Mode`.

```
FixedPageUI [
	# Light Mode
	TextColor = #000000
	BackgroundColor = #ffffff

	# Dark Mode
	# TextColor = #ffffff
	# BackgroundColor = #11141b
	SelectionColor = #f5fc0c
	WindowMargin = 2 4 2 4
	PageSpacing = 4 4
]
```

 Noticed that by changing the Backgroundcolor and MainWindowBackground lines in the Sumatra configuration, we can make our PDF appear in any color we want. If we want to customize Sumatra to match the colors of our Sublime theme, we just need to know the Hex code of the color associated with the theme (i.e. the background color of Sublime). To do this, we can take a screenshot of an area of the screen where the color we want to use is visible, save the image, and use a tool that detects the color in the image ([You can use this](https://imagecolorpicker.com/)).

The color i'm using is for Ayu-Dark.

# Build

To build your LaTeX project, press `Ctrl+Shift+B` and select PDFLaTeX or LuaLaTeX or XeLaTeX depending on which compiler your project requires.

After the first compilation, you should be able to compile simply by using `Ctrl+B`

To compile the project, you need to do it from the main file of the project (for example, main.tex). However, if you want to work on a large project with different .tex files and you don't want to switch to main.tex every time you compile, you can add the following line of code to the file from which you want to compile

```
%!TEX root = main.tex
```

For example: This proyect

![Alt text](/images/Project.png "Path")

If you're working on the 2.5.tex file and want to compile the entire project from there, you need to add %!TEX root = main.tex to the first line, as shown below:

![Alt text](/images/example.png "Path")

The first line of code doesn't affect our project as it is a comment. What it does is tell LatexTools to compile the main.tex file instead of the 2.5.tex file. If your main file isn't named main, you can edit the line of code with the name of your file.

# Some issues

When you start using the interface, you'll notice that when you compile a document, a new Sublime Text window opens. This can be quite annoying, and there may be errors such as auto-completion failures and deleted characters. Here, we will provide solutions to these issues.

* Go to `Preferences -> Package Settings -> LaTeXTools-> Settings-User` and in the line:

```json
"keep_focus": true
```
Change true for false and that will fix the first issue.

Now for auto-completion failures:

* Press `Ctrl+Shift+P` and write `Browse Packages`.

* Open LaTeXTools/latex_cwl_completion.py
* Delete or comment out lines 308–312

```python
if is_prefixed:
    completions = [
        (c[0], c[1][1:]) if c[1].startswith("\\") else c
        for c in completions
    ]
```

Deleting or commenting out these lines of code will solve all the problems.

# Spanish

To add the Spanish language to Sublime Text and the spell checker, you need to download the "Language - Spanish" folder from the repository and put it in the folder that opens when you run "Browse Packages". Once the language folder is located there, go to Sublime Text `View -> Dictionary -> Language - Spanish -> Spanish`. When you select this, Sublime Text will implement Spanish language correction.

The procedure is similar for autocorrection in English, however, you will need to search for the dictionaries as I do not have them available.

# Contact

If you have any issues with the solutions presented here, feel free to ask me:

* mmanosalva@unal.edu.co
* matemano6@gmail.com
