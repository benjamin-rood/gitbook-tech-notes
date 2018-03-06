# Homebrew: Search, install one-liner

Yesterday I wanted to install all the Nerd Fonts not currently on my machine in one go.

`brew cask search fonts`  would give me multiple rows in results – similar to the default output from `ls` :

```
brpro ➜  ~ brew cask search font
==> Partial Matches
birdfont                                      font-hack-nerd-font                           font-noto-sans-thaana
dfontsplitter                                 font-hack-nerd-font-mono                      font-noto-sans-thai
font-3270                                     font-halant                                   font-noto-sans-tibetan
font-3270-nerd-font ✔                         font-hammersmith-one                          font-noto-sans-tifinagh
font-3270-nerd-font-mono ✔                    font-han-nom-a                                font-noto-sans-ugaritic
font-abeezee                                  font-hanalei                                  font-noto-sans-vai
font-abel                                     font-hanalei-fill                             font-noto-sans-yi
font-aboriginal-sans                          font-hanamina                                 font-noto-serif
font-aboriginal-serif                         font-handlee                                  font-noto-serif-armenian
font-abril-fatface                            font-hanuman                                  font-noto-serif-bengali
font-accordance                               font-happy-monkey                             font-noto-serif-cjk
font-aclonica                                 font-hasklig                                  font-noto-serif-cjk-jp
font-acme                                     font-hasklig-nerd-font                        font-noto-serif-cjk-kr
font-actor                                    font-hasklig-nerd-font-mono                   font-noto-serif-cjk-sc
font-adamina                                  font-headland-one                             font-noto-serif-cjk-tc
font-adinatha-tamil-brahmi                    font-heavydata-nerd-font ✔                    font-noto-serif-devanagari
font-advent-pro                               font-heavydata-nerd-font-mono                 font-noto-serif-display
(...)
```

Piping the output to `grep -i nerd` gives a single line-separated list of what we want:

```
brpro ➜  ~ brew cask search font | grep -i nerd
font-3270-nerd-font
font-3270-nerd-font-mono
font-anonymouspro-nerd-font
font-anonymouspro-nerd-font-mono
font-arimo-nerd-font
font-arimo-nerd-font-mono
font-aurulentsansmono-nerd-font
font-aurulentsansmono-nerd-font-mono
font-bitstreamverasansmono-nerd-font
font-bitstreamverasansmono-nerd-font-mono
font-codenewroman-nerd-font
font-codenewroman-nerd-font-mono
font-cousine-nerd-font
font-cousine-nerd-font-mono
font-dejavusansmono-nerd-font
font-dejavusansmono-nerd-font-mono
font-droidsansmono-nerd-font
font-droidsansmono-nerd-font-mono
font-fantasquesansmono-nerd-font
font-fantasquesansmono-nerd-font-mono
font-firacode-nerd-font
font-firacode-nerd-font-mono
font-firamono-nerd-font
font-firamono-nerd-font-mono
(...)
```

We can use `tr` to convert this output to a single line:

```
brpro ➜  ~ brew cask search font | grep nerd | tr '\n' ' '
font-3270-nerd-font font-3270-nerd-font-mono font-anonymouspro-nerd-font font-anonymouspro-nerd-font-mono font-arimo-nerd-font font-arimo-nerd-font-mono font-aurulentsansmono-nerd-font font-aurulentsansmono-nerd-font-mono font-bitstreamverasansmono-nerd-font (...)
```

Now we just need to pass the result to `brew install`:

```
brew install $(brew cask search font | grep nerd | tr '\n' ' ' )
```

Pipe! Composition! Joy!

![](https://media.giphy.com/media/H01rQOhJLjyak/giphy.gif)

The Unix Way.

