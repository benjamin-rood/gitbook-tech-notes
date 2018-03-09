# Homebrew: Search, install all matches, in one-liner

---

#### Syntax:

```
brew install $( brew search my-search-term | grep my-filter-term | tr '\n' ' ' )
```

vs.

```
brew search x | grep y > install_list.txt
brew install < install_list.txt
```

vs.

```
brpro ➜  ~ brew search x
==> Searching local taps...
x ✔                                     xy                                xeme
(...)
==> Searching taps on GitHub...
caskroom/something/xylophone            caskroom/somethingelse/xanthous
(...)
brpro ➜  ~ brew install xeme
```

_Alternative \(using awk\):_

```
brew search x | awk '/inclusion string/ && !/exclusion string/' | tr '\n' ' ' )
```

---

Yesterday I wanted to install all the Nerd Fonts not currently on my machine in one go.

`brew cask search fonts` will give multiple rows in results – similar to the default output from `ls` :

```
brpro ➜  ~ brew cask search font
==> Partial Matches
birdfont                                      font-hack-nerd-font                           font-noto-sans-thaana
dfontsplitter                                 font-hack-nerd-font-mono                      font-noto-sans-thai
font-3270                                     font-halant                                   font-noto-sans-tibetan
font-3270-nerd-font ✔                         font-hammersmith-one                          font-noto-sans-tifinagh
font-3270-nerd-font-mono ✔                    font-han-nom-a                                font-noto-sans-ugaritic
font-abeezee                                  font-hanalei                                  font-noto-sans-vai
(...)
```

Piping the output to `grep -i nerd` gives a single line-separated list of only the _taps_ we want.

```
brpro ➜  ~ brew cask search font | grep -i nerd
font-3270-nerd-font
font-3270-nerd-font-mono
font-anonymouspro-nerd-font
font-anonymouspro-nerd-font-mono
font-arimo-nerd-font
font-arimo-nerd-font-mono
font-aurulentsansmono-nerd-font
(...)
```

We can use `tr` to convert this output to a whitespace-separated single line:

```
brpro ➜  ~ brew cask search font | grep nerd | tr '\n' ' '
font-3270-nerd-font font-3270-nerd-font-mono font-anonymouspro-nerd-font font-anonymouspro-nerd-font-mono font-arimo-nerd-font font-arimo-nerd-font-mono font-aurulentsansmono-nerd-font font-aurulentsansmono-nerd-font-mono font-bitstreamverasansmono-nerd-font (...)
```

Now we just need to pass the result to `brew install`:

```
brew install $( brew cask search font | grep nerd | tr '\n' ' ' )
```

Pipes! Composition! Joy!

![](https://media.giphy.com/media/H01rQOhJLjyak/giphy.gif)

_La voie Unix!_

---

#### Postscript

_Negative \(exclusion\) filtering:_

```
(some command) | grep 'include string' | grep -v 'exclude string'
```

```
(some command) | awk '/include string/ && !/exclude string/'
```



