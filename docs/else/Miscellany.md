---
noindex: true
search:
  exclude: true
---

# Miscellany

## System-related

- **Create USB for multi-boot systems**: <https://linuxkamarada.com/en/2020/07/29/ventoy-create-a-multiboot-usb-drive-by-simply-copying-iso-images-to-it/>
- **Format USB to normal**: <https://averagelinuxuser.com/how-to-format-bootable-usb-to-normal/>
- **App for backup**: <https://www.duplicati.com/>
- **Move Downloads folder to iCloud**: <https://medium.com/@axelsegebrecht/how-to-move-the-mac-downloads-folder-to-icloud-drive-9c513394f3c2>

## Matlab

- **How to execute Matlab via commandline in Linux**: <https://stackoverflow.com/questions/38723138/matlab-execute-script-from-linux-command-line>
- <https://uk.mathworks.com/help/matlab/ref/matlablinux.html>
- **How to set up number of workers for parallel computing in Matlab**: <https://uk.mathworks.com/matlabcentral/answers/1594159-how-many-workers-can-i-use-in-parallelization>

## Industry fellowship

- Apple Scholars in AI/ML PhD Fellowship: <https://www.mpls.ox.ac.uk/graduate-school/funding-for-graduate-students/google-phd-fellowship-and-apple-scholars-in-ai-ml-phd-fellowship-1/google-phd-fellowship-and-apple-scholars-in-ai-ml-phd-fellowship/apple-scholars-in-ai-ml-2022-phd-fellowship-nomination-guidelines>
- **Google PhD fellowship**: <https://research.google/outreach/phd-fellowship/>

## Google spreadsheet

- **Conditional formatting**: `=$g105`, more details see [here](https://support.google.com/docs/answer/78413).

## Camera

- **How does a DSLR camera work**: <https://www.youtube.com/watch?v=W34sLbAsFhM>
- **Nikon D7500 review**: <https://www.youtube.com/watch?v=VpIW0_0MQEg>
- **Mirrorless or DSLR**: <https://shotkit.com/mirrorless-vs-dslr-camera-buyers-guide/>

## Principle of research

- [Orthogonalization](https://www.coursera.org/learn/machine-learning-projects/lecture/FRvQe/orthogonalization)
- [Premature optimization](http://wiki.c2.com/?PrematureOptimization)

## Image editor

- **Clean image**: Create - PhotoRoom
- **Colour picker**: <https://imagecolorpicker.com/>

## Conferences

- **Conference deadlines**: <https://aideadlin.es/?sub=ML,CV>
- **Conference**: <https://www.aminer.org/conf>
- <https://ddl.zepengzhang.com/>

## Concerts

- <https://studentpulselondon.co.uk/index.php/all-events?start=0>

## Catch crayfish in the UK

- **Tutorial**: <https://www.youtube.com/watch?v=m1s-oMKbxJc>
- **American crayfish habitat**: <https://www.wildfoodie.co.uk/post/american-signal-crayfish-how-where-and-when-to-catch-them>
- **Apply for the license**: <https://www.gov.uk/guidance/permission-to-trap-crayfish-eels-elvers-salmon-and-sea-trout> / <https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/936387/Application_to_trap_and_or_remove_crayfish_in_England.pdf>
- **UK grid reference**: <https://gridreferencefinder.com/>
- **Where to find crayfish**: <https://www.naturespot.org.uk/species/signal-crayfish>

## Driving license in the UK

- <https://www.gov.uk/learn-to-drive-a-car>
- **Apply for a provisional driving licence online**: <https://www.gov.uk/apply-first-provisional-driving-licence>
- **Car driving test**: <https://www.gov.uk/guidance/understanding-your-driving-test-result/car-driving-test>
- **Driving test record**: <https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/1082390/dl25-driving-test-report.pdf>
- **Chrome extension for booking a driving test**: <https://www.reddit.com/r/LearnerDriverUK/comments/15waafm/chrome_extension_to_help_book_tests_move_forward/>

## Printer

- Tutorial on how to use the printer at the University of Leicester is available [here](https://uniofleicester.sharepoint.com/sites/get-it-help/SitePages/print.aspx).

## Travel

- [Morocco](Travelmorocco.md)
- **Spain visa application**: <https://www.reddit.com/r/SchengenVisa/comments/17xqm8f/anyone_else_unable_to_upload_their_photo_on_bls/>

## Google add-on

- **How to update**: <https://developers.google.com/apps-script/add-ons/how-tos/update-published-add-on>

## Statistics

- **R + RStudio install**: <https://formulae.brew.sh/cask/rstudio>
- When a normal distribution assumption or central limit theorem holds for each group of data, we can use a parametric hypothesis test, such as a t-test.
- Otherwise, we can use a nonparametric hypothesis test, which is also called a distribution-free test, e.g., Wilcoxon signed-rank test.
- If two groups are dependent, we should use, for example, a paired Wilcoxon signed-rank test.
- A nice discussion about how to choose a hypothesis test is available [here](https://stats.stackexchange.com/questions/121852/how-to-choose-between-t-test-or-non-parametric-test-e-g-wilcoxon-in-small-sampl) and [here](https://www.sciencedirect.com/topics/medicine-and-dentistry/nonparametric-test).

## Web scraping

- **Web Scraping Using Selenium Python**: <https://iqss.github.io/dss-webscrape/>

## Isambard HPC setup

SSH key is simply generated via `ssh-keygen`.

```
Host isambard2
  Hostname ai-p2.access.isambard.ac.uk
  User yz681.u6in
  CertificateFile "/Users/yihang/Library/Caches/clifton/u6in.aip2.isambard-cert.pub"
  ProxyJump yz681.u6in@jump.u6in.aip2.isambard
  IdentityFile "/Users/yihang/.ssh/sulis"
  AddKeysToAgent yes
```

First run `clifton auth --identity .ssh/sulis`, then run `ssh isambard2` to login.

[Back to Else](index.md)
