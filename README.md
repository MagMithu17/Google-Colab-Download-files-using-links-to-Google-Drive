<a href="https://colab.research.google.com/github/MagMithu17/Google-Colab-Download-any-links-to-Google-Drive/blob/main/Download_files_from_links.ipynb">
  <img src="https://colab.research.google.com/assets/colab-badge.svg" alt="Open In Colab"/>
</a><br>

# Google-Colab-Download-files-from-links-to-Google-Drive
It will support both static and dynamic links.<br>
Three methods are availabe to do this process<br>
Firefox browser is mandatory to do 2nd and 3rd method and you need to disable other third party downloaders like IDM for method 2.<br>
You can disable IDM with disabling IDM addon

### First method - Normal Link
In this method you can easily copy and paste direct links from IDM or Chrome or Firefox but It will support for static links only<br>
![Alt Text](https://i.ibb.co/vLj1bXR/Normal-link-download-using-IDM.gif)

### Second method - Firefox_cliget_wget_link         
First you need to add cliget addon on firefox.<br> cliget addon link : https://addons.mozilla.org/en-US/firefox/addon/cliget/<br>
![Alt Text](https://i.ibb.co/QDr1QNq/Firefox-CLI-get-download.gif)


### Third method - Firefox_Command_Line_Get_Curl_Link
First you need to add Command_Line_Get addon on firefox.<br> Command_Line_Get addon link : https://addons.mozilla.org/en-US/firefox/addon/command-line-get-clg/<br>
This method will create a web url from download buttons 
![Alt Text](https://i.ibb.co/tLnYyr2/Command-Line-Get-download.gif)
<br><br>
cell codings <br>
```
#@title <font color ="yellow">`⬅`</font><font color="#01c968">`Download from Link`</font>
#@markdown <font color ="red"><h6>`In "Firefox_cliget_wget_link" and "Firefox_Command_Line_Get_Curl_Link" method you can't edit Downloading file name using "File_Name" field`</h6>
def first4(s):
    return s[:4]
import os
Download_Link_Model = "Normal_Link" #@param ["Normal_Link", "Firefox_cliget_wget_link", "Firefox_Command_Line_Get_Curl_Link"] 

Download_Location = "/content/drive/MyDrive/Downloads" # @param {type:"string"}
if not Download_Location.strip():
  Download_Location = "/content"
from pathlib import Path
Path(Download_Location).mkdir(parents=True, exist_ok=True)
os.chdir(Download_Location)
Link = "" # @param {type:"string"}
File_Name = "" # @param {type:"string"}
if Download_Link_Model=="Firefox_cliget_wget_link":
  cliget_link = Link.strip()
  chk = first4(cliget_link)
  if chk=="wget":
    cliget_link = cliget_link[5:]  
  !wget -c $cliget_link --no-check-certificate
elif Download_Link_Model=="Firefox_Command_Line_Get_Curl_Link":
  CLG_Curl_Link = Link.strip()
  !$CLG_Curl_Link
else:
  if not File_Name.strip(): 
    !wget -c "$Link" --no-check-certificate
  else:  
    !wget -c "$Link" -O "$File_Name" --no-check-certificate
```
