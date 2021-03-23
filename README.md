# uwu
fastest text uwu-ifier in the west

## faq
### what?
u want large amounts of text uwu'd in a smol amount of time

### where?
your computer, if it has a recent x86 cpu (intel, amd) that support sse4.1

### why?
why not?

### how?
tldr: 128-bit simd vectorization plus some big brain algos

after hours of research, i've finally understood the essence of uwu'd text

there are a few transformations:
1. nya-ify (eg. `naruhodo` -> `nyaruhodo`)
2. replace `l` and `r` with `w`
3. stutter sometimes (`hi` -> `h-hi`)
4. add a text emoji after punctuation (`,`, `.`, or `!`) sometimes
5. replace some words (`small` -> `smol`, etc.)

these transformation passes take advantage of sse4.1 vector intrinsics to process 16 bytes at once.
for string searching, i'm using a custom simd implementation of the
[bitap](https://en.wikipedia.org/wiki/Bitap_algorithm) algorithm for matching against multiple strings.
for random number generation, i'm using [XorShift32](https://en.wikipedia.org/wiki/Xorshift). for most
character-level detection within simd registers, its all masking and shifting to simulate basic state
machines in parallel

multithreading is supported, so you can exploit all of your cpu cores for the noble goal
of uwu-ing massive amounts of text

utf-8 is handled elegantly by simply ignoring non-ascii characters in the input

unfortunately, due to both simd parallelism and multithreading, some words may not be fully uwu'd
if they were lucky enough to cross the boundary of a simd vector or a thread's buffer.
*they won't escape so easily next time*

### ok i want uwu'd text, how do i run this myself?
1. install rust: run `curl https://sh.rustup.rs -sSf | sh` unix,
or go [here](https://www.rust-lang.org/tools/install) for more options
2. clone this repo
3. idk

### why isn't this readme uwu'd?
so its readable

if u happen to find uwu'd text more readable, there's always an [uwu'd](README_UWU.md) version

### ok but why aren't there any of the settings i can change?!1?!!1
free will is an illusion

### wtf this is so unprofessional how are u gonna get hired at faang now?!
don't worry, i've got u covered

**Title: uwu is all you need**

**Abstract:**

Recent advances in computing have made strides in parallelization, whether
at a fine-grained level with SIMD instructions, or at a high level with multiple
CPU cores. Taking advantage of these advances, we explore how the useful
task of performing an uwu transformation on plain text can be scaled up to large
input datasets. Our contributions in this paper are threefold: first, we present,
to our knowledge, the first rigorous definition of uwu'd text. Second, we show
our novel algorithms for uwu-ing text, exploiting vectorization and
multithreading features that are available on modern CPUs. Finally, we provide
rigorous experimental results that show how our implementation could be the
"fastest in the west." In our benchmarks, we observe that our implementation
was almost as a fast as a simple file copy, which is entirely IO-bound.
We believe our work has potential applications in various domains, from data
augmentation and text preprocessing for natural language processing, to
giving authors the ability to convey potentially wholesome or cute meme messages
with minimal time and effort.

*// TODO: write paper*
*// TODO: write more about machine learning so i get funding*

### ok i need to use this for something and i need the license info
mit license

### ok but i have an issue with this or a suggestion or a question not answered here
open an issue, be nice

### references
* https://honk.moe/tools/owo.html
* https://github.com/IamRifki/uwuizer
* https://cutekaomoji.com/characters/uwu/
* https://cutekaomoji.com/characters/owo/
* https://cutekaomoji.com/characters/flower-girl/
* and many more; let me know if i missed anything
