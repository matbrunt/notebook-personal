# OS Tips

## Joining PDFs

https://stackoverflow.com/questions/434248/is-it-possible-to-programmatically-chain-several-pdf-files-preferably-from-co

ghostcript method:

gs -q -sPAPERSIZE=letter -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -sOutputFile=out.pdf in1.pdf in2.pdf in3.pdf ...
from: How to concatenate PDFs without pain

ImageMagick method:

convert file1.pdf file2.pdf file3.pdf out.pdf
pdftk method:

pdftk file1.pdf file2.pdf file3.pdf cat output out.pdf