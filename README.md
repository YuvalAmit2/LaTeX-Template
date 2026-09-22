Welcome! Here's a quick tutorial on how to use my template.

# Modes

This template has three modes:
* Notes mode: used for course notes and problem sets. Prioritizes readability. Code in notes_settings folder.
* Paper mode: used for papers (duh). Code in paper_settings folder.
* Presentation mode: used for beamer presentations. Code in presentation_settings folder.

These are also listed in order of how "complex" I've made them. I use Notes mode almost every day as a student, so it has tons of very tuned functionality. Paper mode is also pretty good, and Presentation mode is my least customized. 

If you are using this template on your own, you can switch between these three modes by commenting and uncommenting the corresponding code at the top of main.tex.

If you're collaborating with me on something, chances are we're already in the correct mode, so no need to mess with it.

# Commands

Like most templates, this one has a large list of custom commands. Note that the file main.tex includes almost all my commands for writing math. Normally, this is something one would put in a preamble file, but I write primarily with Overleaf's live math display in the text editor, which requires me to define those commands in the same document I write in. If you're using this template in almost any other way, I'd recommend moving these to preamble.tex or elsewhere.

I initially wanted to make a table of all the custom commands I have, but most of the time you can just scroll to the top of main.tex to see what's there, so that doesn't really make sense. Here's just a few notable commands:
* Blackboard bold is just a single letter: e.g. \Z = $\mathbb{Z}$.
* Letters without preset blackboard bold can be quickly bb'd with \mb{\<letter\>}
* Similarly, \mc gives mathcal and \mf gives mathfrak
* \bar{}, \hat{}, and \tilde{} have all been reset to their wide versions
* \matr{} is a pmatrix, \case{} is cases, \leg{}{} is Legendre symbol
* \partder[a]{b}{c} is $\frac{\partial ^ ab}{\partial ^ac}$
* \arr, \inj, \surj, and \maps are all the expected arrows, and each can take an optional argument to go above the arrow. They will grow longer with the argument.
* \brax{} is $\{\}$, \braks{} is $[ ]$, and \angles{}, \floor{}, \paren{}, \abs{}, and \norm{} are as expected. Each has \left and \right built in so they grow.
* \setbar is a vertical bar | which can go in the middle of a \left \right environment to grow if the brackets grow.
* There's a laundry list of commands which just yield text versions of the work like \Span, \Re, \Specm, etc. It's best to just look at main.tex for this.
* \w{} makes the argument upright text in math. 
* \bw{} makes the argument upright bold text in math.

# Theorem-like Environments

## Notes Mode

The biggest difference between Notes mode and Paper mode is the format of theorem-like environments, i.e. theorems, definitions, examples, etc.

In Notes mode, you can make one of these with

```
\begin{<type>}[custom_name][extra_optional_args]
   text
\end{<type>}
```
Here, \<type\> can be: thm, defn, lem, cor, prop, rmk, conj, notethm, ex, que, claim, notethm.

The first optional argument gives the environment a custom name, and the second can be used to make additional changes to the underlying environment. Most commonly, this can be adding a label. For example,

```
\begin{thm}[Fermat's Last Theorem][label=thm:fermat]
    The equation $a^n + b^n = c^n$ has no non-trivial integer solutions for $n>2$
\end{thm}
```
Some environments (thm, defn, lem, cor, prop, rmk, conj) will appear as TColorBox's. The rest (ex, que, claim) appear as typical theorem environments (with some color).

There are also two special environments: notebox and notethm. The first acts as a customizable tcolorbox environment and the second acts as a customizable regular theorem environment. They are used exactly the same as the rest of the thm-likes, but custom_name affects the name of the enviornment differently, as if you did \begin{custom_name}... .

One functionality I don't yet have is better referencing for note_box and note_thm environment. Namely, if you give a notebox or notethm a custom name, and then reference it with Cref, the reference will appear as 'Note' rather than the custom name.

All thm-like environments can be used with a \*, e.g. \begin{thm\*}... to remove the numbering.

Referencing can be done with \Cref{...}. Both the word "theorem" and the number will be hyperlinked.



## Paper Mode

The thm-like situation for Paper mode is similar to that for Notes mode, with a few small usage differences, and big visual differences.

In Paper mode, you create a thm-like with
```
\begin{<type>}[custom_name] \label{lab}
    text
\end{<type>}
```
Here, \<type\> can be thm, prop, rmk, cor, defn, lem, ex, que, exer, conj, note.

The custom_name and the label are optional. 

Note behaves as a special customizable thm-link environment. Rather than adding custom_name in a parenthesis after the type name (e.g. Theorem (custom_name)), it changes the type name.

All thm-like environments can be used with a * to remove the numbering.

## Presentation Mode

When using Beamer, I've found it's best to stick with the native block environments rather than creating custom thm-likes. The block environments look more natural, and don't need fancy features like numbering and referencing. To make a frame (a slide) and a block (a "thm-like"):

```
\begin{frame}{Frame Title}
    \begin{block}{Custom Name}
        Text
    \end{block}
\end{frame}
```
