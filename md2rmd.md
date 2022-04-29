
# step 1  trangform the .md file to .rmd file and open .rmd file in Rsutdio

note:  you should run the following code in Rstuido

```{r}

# this code is for writing code in obsidian app, but open it in Rsutdio.

# package `RSAGA` for change file extension 

library(RSAGA)

# list all .md files in  obsidian vault: `ob_path`

ob_path<-'D:/obsidian/' 

ob_md<-list.files(ob_path,pattern = ('\\.md'),full.names = T)

ob_md

# choose the .md file you wanted to open it in Rstudio

file_num <- 1

# use set.file.expansion function to change .md to .rmd, note this step only 

# change the characters, not really change the file in the next step

md_rmd<-set.file.extension(ob_md[file_num],'rmd')

# copy the  .md  file to .rmd file

file.copy(ob_md[file_num],md_rmd,overwrite = T)

# open .rmd file in Rsutdio

file.edit(md_rmd)

```

# step 2 synchronize  the modifed .rmd file  to .md 

```{r}
# !important: copy the .rmd file in Rstudio  to .md file in obsidian. you should

# execute this code chunk every time after save the  rmd file

library(rstudioapi)

this_file<-getActiveDocumentContext()$path #<- get this file path
 
rmd2md<-set.file.extension(this_file,'.md') #<- change filename from'.rmd' to '.md'

file.copy(this_file,rmd2md,overwrite = T) #<- copy '.rmd' file  to '.md'

```

