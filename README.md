# sillycrypt

Simplest possible cryptosystem

## Idea

Take a Unicode string convert to an ArrayBuffer (only reliable way is to use 32-bit code points).

If data is binary then don't do the first step. 

Convert those words to base64.

Include a header that specifies whether string or binary was starting point, and also the byte length of the input.

Perform encryption using an s-box 6x6, and row/column transposition on a matrix of 1024 (32x32) letters.

Insecure version uses a static s-box and static transpositions.

Secure version uses a keyed s-box, and keyed transpositions.

Take the resulting base64 letters and convert them to base2.

Take that sequence of 'bits' and a source bitmap image, and combine them by first turning every color value in the bitmap to even by rounding down if it's odd. If it's even, then just leave it. Now for each 1 in the sequence of bits, turn that color value odd by rounding it up. To recover the sequence of 'bits', take the image and read off the even values, then reverse the process.
