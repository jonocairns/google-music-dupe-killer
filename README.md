Google Music Dupe Killer
========================

Really small script designed to remove pesky duplicates from Google Music.

** The duplicates must have all correct meta data as this evaluates their title and album for detection.

Thanks to [simon weber](https://github.com/simon-weber) for a GREAT client library that made this super easy to code.

## Usage
This is a incredibly simple script, but does require a few small configurations.

### Install [Unofficial Google Music Api](https://github.com/simon-weber/Unofficial-Google-Music-API)
* For most environments with Python already installed:
   
   ```$ pip install gmusicapi```
* If you do not have pip or are running windows, please see [Unofficial Google Music API usage](http://unofficial-google-music-api.readthedocs.org/en/latest/usage.html)

### Change login credentials
* Near line 89, change the 'username' and 'password' to your Google account credentials.

### Run kill_dupes
* The script will automatically detect and remove duplicates on any songs in your library.


http://android.stackexchange.com/questions/62666/is-there-any-way-to-find-remove-duplicate-tracks-from-google-play-music

From a PC running Windows 10 x64 (64-bit):

Install the latest Python 2.7.x version. (I used Python 2.7.10; Do not use any Python 3.x.y version -- I couldn't get it to work with this script.)
If using Windows, install the Microsoft Visual C++ Compiler for Python 2.7. One of the dependencies of gmusicapi requires it.
Install the Google Music API for Python. You should use "pip" (Python's built-in installer script) to install it. On Windows, pip is not added to the PATH environment variable. The quick, lazy workaround is to invoke it specifically:

C:\Python27\Scripts\pip.exe install gmusicapi
See footnote if you're having issues. LibAV or ffmpeg are probably not required for our purposes.

On the right side of the Google Music Dupe Killer page:

Click "download ZIP" → Extract the ZIP → Rename kill-dupes to kill-dupes.py → Right click → edit with Notepad (or Notepad++, or anything similar) → Ctrl-F ("find") for "username".
On line #89, you'll see this (line numbers added for ease of reading):

88. api = Mobileclient()  
89. logged_in = api.login('username', 'password') 
90.
91. if logged_in:
Replace the word username with your Google username, and the word password with your Google password. Leave the single-quotes ' as-is. Save the file with the edits you made.

Allow less secure apps to access your account via Google. If you don't do this, Google will email you telling that they blocked someone accessing your account the first time you run the script. In that email, there is a link to change the setting.

(Note: you may wish to change it back after you are done with this script.)

Put the modified kill_dupes.py script somewhere you can find it. I put it in C:\Python27\.

Open the Windows command prompt. (Win+R opens the Run dialog, cmd is the command prompt. Press Enter.)

You'll see a Window with this written:

C:\Users\YourWindowsUsername>
Run Python with the script you made:

C:\Users\YourWindowsUsername>c:\Python27\python.exe c:\Python27\kill_dupes.py
Press Enter to run the script:

Successfully logged in. Beginning duplicate detection process.
The program prints a list of the duplicate tracks it found. Type y and press Enter to remove them, or n to not remove them.

kill_dupes.py and maybe its parent program gmusicapi crash on Unicode characters like つんく♂. Here is the bug report. Oddly enough, by running the script from IDLE, it worked fine. IDLE should be included with all Python installs.

IDLE (Python GUI) → file → open → kill_dupes.py

IDLE (Python GUI) → run → run module

If you just see a blank window, you probably forgot to allow less secure apps to access your account. See step 7.

(Optional) Forbid less secure apps from accessing your Google account.

I used the answer by neves to develop this answer.

Footnote: Installing LibAV
This probably isn't required, but it's what I did the first time I did this. I have since successfully removed duplicates without LibAV, but I did have ffmpeg in my PATH already. The reason I say this step isn't required is because the Google Music API website says:
If you’re going to be uploading music, you’ll likely want Libav’s avconv installed and in your system path, along with at least libmp3lame.
Update 2016-01-09: The site now says:

The only time avconv or ffmpeg is not required is when uploading mp3s without scan-and-match enabled.
Use your judgment as to whether or not installing LibAV is needed.

Download the newest (sort by date modified) "nightly-lgpl" x86_64 variant of LibAV. It's linked from the site given in step 2.
I downloaded libav-x86_64-w64-mingw32-20150524.7z → extracted the .7z file → added the /usr/bin folder within the extracted libav folder to the PATH. (The steps are explained in the link in step 2. lat ays to add (Python's built-in installer script) avconv.exe to the PATH. So my computer now has D:\Downloads\libav-x86_64-w64-mingw32-20150524\usr\bin added to its PATH.

Thanks!
