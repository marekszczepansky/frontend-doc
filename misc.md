### PDF preview in new tab

`<a href="myfile.pdf" target="_blank">`

Your server should return this http header:

`Content-Type: application/pdf`

For viewing in browser it should also return:

`Content-Disposition: inline;filename="myfile.pdf"`

For downloading:

`Content-Disposition: attachment;filename="myfile.pdf"`
