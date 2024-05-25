# Korean alt layouts

Idea: 
choose shifted/unshifted/compound keys for a  Korean Hangul layout so as to minimizes total number of keypresses.
Pressing shift counts as one keypress, releasing shift counts as another.
If a sequence of characters can be typed with shift held down through them all
(which is often possible in, say, Dubeolsik, since many keys output the same jamo regardless of whether shift is held down or not),
that counts as pressing shift once.

Methodology:
use the `wordfreq` Python library for word frequencies, 
and the `jamo` library to decompose Hangul words into jamo.
Then I decomposed the jamos into keypresses according to 4 different schemes listed below.
(I represent pressing shift with "S" and releasing with "U".
I omit the entries where the jamo decomposes to itself, e.g. ㅏ → ㅏ in Dubeolsik, regardless of shift state).

Dubeolsik decomposition scheme:
```
"ㄲ": "Sㄱ",
"ㄳ": "Uㄱㅅ",
"ㄵ": "ㄴUㅈ",
"ㄶ": "ㄴㅎ",
"ㄸ": "Sㄷ",
"ㄺ": "ㄹUㄱ",
"ㄻ": "ㄹㅁ",
"ㄼ": "ㄹUㅂ",
"ㄽ": "ㄹUㅅ",
"ㄾ": "ㄹㅌ",
"ㄿ": "ㄹㅍ",
"ㅀ": "ㄹㅎ",
"ㅃ": "Sㅂ",
"ㅄ": "Uㅂㅅ",
"ㅆ": "Sㅅ",
"ㅉ": "Sㅈ",
"ㄱ": "Uㄱ",
"ㄷ": "Uㄷ",
"ㅂ": "Uㅂ",
"ㅅ": "Uㅅ",
"ㅈ": "Uㅈ",
"ㅐ": "Uㅐ",
"ㅒ": "Sㅐ",
"ㅓ": "Uㅓ",
"ㅔ": "Uㅔ",
"ㅖ": "Sㅔ",
"ㅘ": "ㅗㅏ",
"ㅙ": "ㅗUㅐ", # not ㅗㅐ
"ㅚ": "ㅗㅣ",
"ㅝ": "ㅜㅓ",
"ㅞ": "ㅜUㅔ", # not ㅜㅔ
"ㅟ": "ㅜㅣ",
"ㅢ": "ㅡㅣ",
```

Dubeolsik decomposition scheme but I made ㅆ unshifted and ㅠ shifted:
```
"ㄲ": "Sㄱ",
"ㄳ": "Uㄱㅅ",
"ㄵ": "ㄴUㅈ",
"ㄶ": "ㄴㅎ",
"ㄸ": "Sㄷ",
"ㄺ": "ㄹUㄱ",
"ㄻ": "ㄹㅁ",
"ㄼ": "ㄹUㅂ",
"ㄽ": "ㄹUㅅ",
"ㄾ": "ㄹㅌ",
"ㄿ": "ㄹㅍ",
"ㅀ": "ㄹㅎ",
"ㅃ": "Sㅂ",
"ㅄ": "Uㅂㅅ",
# "ㅆ": "ㅅ", unshifted
"ㅉ": "Sㅈ",
"ㄱ": "Uㄱ",
"ㄷ": "Uㄷ",
"ㅂ": "Uㅂ",
"ㅅ": "ㅅ",
"ㅈ": "Uㅈ",
"ㅐ": "Uㅐ",
"ㅒ": "Sㅐ",
"ㅓ": "Uㅓ",
"ㅔ": "Uㅔ",
"ㅖ": "Sㅔ",
"ㅜ": "Uㅜ",
"ㅠ": "Sㅜ",
"ㅘ": "ㅗㅏ",
"ㅙ": "ㅗㅐ", # ㅗㅒ isn't valid anyways
"ㅚ": "ㅗㅣ",
"ㅝ": "ㅜㅓ",
"ㅞ": "ㅜㅔ", # ㅠㅖ isn't valid anyways
"ㅟ": "ㅜㅣ", # ㅠㅣ isn't valid anyways
"ㅢ": "ㅡㅣ",
```

(The motivation for this is that ㅆ is more frequent than ㅠ.)

Dubeolsik decomposition scheme but I made ㅆ unshifted and ㅠ shifted and also many composite vowel jamos are shifted.
```
"ㅣ": "Uㅣ",
"ㅡ": "Uㅡ",
"ㅏ": "Uㅏ",
"ㅐ": "Uㅐ",
"ㅑ": "Uㅑ",
"ㅓ": "Uㅓ",
"ㅔ": "Uㅔ",
"ㅕ": "Uㅕ",
"ㅗ": "Uㅗ",
"ㅜ": "Uㅜ",
"ㄱ": "Uㄱ",
"ㄷ": "Uㄷ",
"ㅂ": "Uㅂ",
"ㅈ": "Uㅈ",
"ㅆ": "Uㅆ",
"ㅟ": "Sㅣ", # notice all the composite vowels on the shift layer now
"ㅢ": "Sㅡ",
"ㅘ": "Sㅏ",
"ㅙ": "Sㅐ",
"ㅒ": "Sㅑ",
"ㅝ": "Sㅓ",
"ㅞ": "Sㅔ",
"ㅖ": "Sㅕ",
"ㅚ": "Sㅗ",
"ㅠ": "Sㅜ",
"ㄲ": "Sㄱ",
"ㄸ": "Sㄷ",
"ㅃ": "Sㅂ",
"ㅉ": "Sㅈ",
"ㄶ": "ㄴㅎ",
"ㅄ": "ㅂㅅ",
"ㄺ": "ㄹㄱ",
"ㅀ": "ㄹㅎ",
"ㄻ": "ㄹㅁ",
"ㄼ": "ㄹㅂ",
"ㄵ": "ㄴㅈ",
"ㄳ": "ㄱㅅ",
"ㄾ": "ㄹㅌ",
"ㄿ": "ㄹㅍ",
```

(The motivation here was that I realized that my metric always counts shift keys as not worse than two consecutive keypresses.)

A scheme I made up where yin vowels are shifted and yang vowels are unshifted:
```
"ㄳ": "ㄱㅅ",
"ㄵ": "ㄴㅈ",
"ㄶ": "ㄴㅎ",
"ㄺ": "ㄹㄱ",
"ㄻ": "ㄹㅁ",
"ㄼ": "ㄹㅂ",
"ㄽ": "ㄹㅅ",
"ㄾ": "ㄹㅌ",
"ㄿ": "ㄹㅍ",
"ㅀ": "ㄹㅎ",
"ㅄ": "ㅂㅅ",
"ㅏ": "Uㅏ",
"ㅐ": "Uㅏㅣ",
"ㅑ": "Uㅑ",
"ㅒ": "Uㅑㅣ",
"ㅓ": "Sㅏ",
"ㅔ": "Sㅏ",
"ㅕ": "Sㅑ",
"ㅖ": "Sㅑㅣ",
"ㅗ": "Uㅗ",
"ㅘ": "Uㅗㅏ",
"ㅙ": "Uㅗㅏㅣ",
"ㅚ": "Uㅗㅣ",
"ㅛ": "Uㅛ",
"ㅜ": "Sㅗ",
"ㅝ": "Sㅗㅏ",
"ㅞ": "Sㅗㅏㅣ",
"ㅟ": "Sㅗㅣ",
"ㅠ": "Sㅛ",
"ㅢ": "ㅡㅣ",
```

(The motivation for this is that I read that Korean has traces of vowel harmony.
For one, this ensures that all digraphs will only need SHIFT to be pressed once instead of twice.
But maybe this is counterproductive because vowel harmony in vowel digraphs mean we could set up a method for deducing one vowel from the other.
i.e., a sequence like ㅗㅓ could always be translated to ㅘ. 
And, yotated vowels don't really participate in a digraphs (only in ㅒㅖ), so that's another source of needless effort.
Hm... but then having it be too intelligent sounds like it'd be annoying and also not really correspond closely to actual writing.)

After decomposing according to the scheme, I then removed consecutive "U"/"S", i.e. to represent shift be held down / left up.
If a word could be typed entirely with shift held down, I didn't count that as adding any additional keypresses, 
which probably biases schemes that use shift more.

(Example:
`쌍시옷` decomposes into `ㅆㅏㅇㅅㅣㅇㅗㅅ` as jamo,
which then decomposes into `SㅅㅏㅇUㅅㅣㅇㅗㅅ` with the Dubeolsik layout.
Then, we assume it costs us nothing to hold shift down during space, so we get rid of that first `S`, giving us
`ㅅㅏㅇUㅅㅣㅇㅗㅅ`, so this counts as 9 keypresses.)

Then I multiplied the number of keypresses for that word by its `word_frequency`, and then summed that over the top 200,000 words (which gives me the same results as doing over the top 1,000,000 words).

## Results

| decomposition scheme | frequency per word * keypresses |
|--|--|
| Dubeolsik (ㅠㅆ and many vowels altered) | 3.465424509999993 |
| Dubeolsik (ㅠㅆ altered) | 3.4722890599999916 |
| Dubeolsik | 3.485696489999989 |
| "Yinyang" | 3.618027129999951 |

It seems that the average word is 3.4 keypresses long. 
Basically Dubeolsik is pretty good already: the principle of assigning the least common jamo to the shift layer seems superior.

## Appendix: Jamo frequencies
I calculated the jamo frequencies as follows:
```
ㅇ: 0.41581721999998983
ㅏ: 0.29316436999999196
ㄴ: 0.2850557999999967
ㅣ: 0.21870247000000134
ㄱ: 0.21514189999999975
ㄹ: 0.2080710600000001
ㅡ: 0.16788782000000002
ㅓ: 0.13152134000000137
ㅗ: 0.13039939000000106
ㅅ: 0.12848920999999916
ㄷ: 0.12065218000000187
ㅈ: 0.1158025700000026
ㅁ: 0.10268237000000252
ㅎ: 0.10245599000000172
ㅜ: 0.08175110000000226
ㅂ: 0.07710729000000222
ㅔ: 0.07408668000000118
ㅐ: 0.06501342999999969
ㅕ: 0.057538750000000166
ㅆ: 0.03702303000000007
ㅊ: 0.029971209999999943
ㅌ: 0.026100009999999934
ㅘ: 0.023027909999999974
ㅍ: 0.02076382999999991
ㅢ: 0.020542429999999997
ㅛ: 0.019754479999999956
ㅚ: 0.014595509999999999
ㅋ: 0.012257760000000034
ㅝ: 0.012033050000000031
ㅑ: 0.010225620000000015
ㄲ: 0.009790190000000015
ㄸ: 0.008467390000000023
ㅠ: 0.007501269999999983
ㅟ: 0.00702484999999999
ㅖ: 0.0055864399999999885
ㄶ: 0.004506620000000001
ㅄ: 0.0033015299999999987
ㅉ: 0.00292821
ㅙ: 0.0023109399999999983
ㅃ: 0.0022877499999999977
ㄺ: 0.0006371199999999998
ㅞ: 0.0005492300000000004
ㅀ: 0.0005296900000000002
ㅒ: 0.00043731000000000005
ㄻ: 0.0004109800000000001
ㄼ: 0.00022739
ㄵ: 0.00015746999999999997
ㄳ: 2.7289999999999998e-05
ㄾ: 9.129999999999999e-06
ㄿ: 4.27e-06
```
Also see [https://story.pxd.co.kr/958] (but I can't read Korean, so I just looked at the digrams). I also "don't believe in" alternating-hand shift (I find it mostly fine to hold shift with the same hand as it presses other keys).
