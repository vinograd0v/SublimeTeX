# SublimeTeX

![GitHub all releases](https://img.shields.io/github/downloads/mmanosalva/SublimeTeX/total?logo=github&style=plastic)
![GitHub repo size](https://img.shields.io/github/repo-size/mmanosalva/SublimeTeX)

This is a LaTeX setup guide for Sublime Text with LaTeXTools. In this repository, you will find solutions to all the problems that usually arise when installing this package, as well as a customization guide.

  ![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Workstation.png)


# Download:

- [Sublime text here.]( https://www.sublimetext.com/)
- [MiKTeX here.](https://miktex.org/download)
- [Sumatra PDF here.](https://www.sumatrapdfreader.org/download-free-pdf-viewer)
- [ImageMagick here.](https://imagemagick.org/script/download.php#windows)


# Install

- Install Sumatra first and then MiKTeX and then ImageMagick. Finally install Sublime Text. Make sure that ImageMagick is added to the Windows Path during installation. The option should be checked during installation. Additionally, SumatraPDF must also be added to the Path. However, you must do this manually by finding the installation folder of SumatraPDF and adding it to the Path.
  
  ![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Path.png)

 If you don't see ImageMagick in the Windows Path, add it manually by copying the path and pasting it, just like with Sumatra.

  Before we proceed, it may be necessary to install some LaTeX packages from MiKTeX. To do this, we need to open the MiKTeX console.

  * Go to Packages and install "preview" and "mathtools" as below:
  
   ![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Miktex.png)

   * You should type the names of the packages in the selected part.
   * Now install:

 ![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Preview.png)

 Once both packages are installed, proceed with the installation, remember that in the future compiling one of your projects may require a package that you may have to install from this console.

Also, it may be recommended to enable automatic package installation: Go to Setting

 ![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Conf.png)

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

- Save the file. This will automatically install all the packages necessary for the setup.  Wait for 5-10 mins for the installation to complete (be sure the installation complete).

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

 ![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Compilers.png)

 If you don't use those you can maybe have problems with biblatex.

After the first compilation, you should be able to compile simply by using `Ctrl+B`

To compile the project, you need to do it from the main file of the project (for example, main.tex). However, if you want to work on a large project with different .tex files and you don't want to switch to main.tex every time you compile, you can add the following line of code to the file from which you want to compile

```
%!TEX root = main.tex
```

For example: This project

![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Project.png)

If you're working on the 2.5.tex file and want to compile the entire project from there, you need to add %!TEX root = main.tex to the first line, as shown below:

![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Example.png)

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

## Biblatex:

There is an issue that occurs when using biblatex and not making any citation in the entire document, basically it does not print the bibliography and the "\nocite{*}" command does not work. Once we make at least one citation in the entire document, the "\nocite{ * }" command works and the problem is fixed. However, if we do not want to make any citation in the entire document, a quick solution for this is to make a phantom citation, that is, one that does not affect the final document but solves the problem. To do this, we implement the following in our .tex file:

```tex
\newcommand{\phantomcite}[1]{
    \phantom{\cite{#1}}
    \nocite{*}
}
```

So at the end of our document, before using "\printbibliography", we put the command "\phantomcite{"here put any citation from your references"}" and that will solve the problem. This command executes a phantom citation and is followed by the "\nocite{*}" command, so it will no longer be necessary to use it.

* Example:
  
```tex
\documentclass{article}

\usepackage{biblatex}

\newcommand{\phantomcite}[1]{
    \phantom{\cite{#1}}
    \nocite{*}
}


\addbibresource{sample.bib}

\begin{document}

Test. 

\phantomcite{dirac}

\printbibliography
\end{document}
```

Another way to fix the problem is before using "\nocite{*}" put "nocite{"some of your reference"}":

```tex
\documentclass{article}

\usepackage{biblatex}

\addbibresource{sample.bib}

\begin{document}

Test. 

\nocite{dirac}
\nocite{*}

\printbibliography
\end{document}
```

As mentioned earlier, the problem is related to "\nocite{*}". In this solution, it is not necessary to add the "\phantomcite" from the previous solution.

* IMPORTANT: If you compile your project and it generates the bibliography and you make changes to it, you may need to delete the generated files and compile again. Otherwise, the bibliography may not change. The corresponding file is the one with the extension .bbl in our files folder.



# Spanish

To add the Spanish language to Sublime Text and the spell checker, you need to download the "Language - Spanish" folder from the repository and put it in the folder that opens when you run "Browse Packages". Once the language folder is located there, go to Sublime Text `View -> Dictionary -> Language - Spanish -> Spanish`. When you select this, Sublime Text will implement Spanish language correction.

The procedure is similar for autocorrection in English, however, you will need to search for the dictionaries as I do not have them available.

# ImageMagick Preview:

With this project you will be able to see your equations without compile:

![Alt text](https://github.com/mmanosalva/SublimeTeX/blob/main/Images/Previeww.png)

If you see the resolution of the preview is too low go to: `Preferences -> Package Settings -> LaTeXTools-> Settings-User` and then search for the line "preview_math_density", you can change values and prove some resolutions and pixeles density if you want, this is my config for my screen (2160x1440p):

```json
	// The density of the preview image. The higher the density the bigger the phantom.
	"preview_math_density": 300,
	// If the image is not sharp enough increase this scale to get a better resolution.
	// However also change the density by the same factor to keep the size.
	"preview_math_scale_quotient": 3,
	// If this is true, the image will be rendered at a higher resolution and
	// then scaled down. This generally results in a clearer image.
	"preview_math_hires": true,
```



# Contact

If you have any issues with the solutions presented here, feel free to ask me:

* mmanosalva@unal.edu.co
* matemano6@gmail.com
