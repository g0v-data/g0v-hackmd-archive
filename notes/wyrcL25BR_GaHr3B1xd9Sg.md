How to Install whisper in Macbook


1. Open the terminal (Input "terminal" in Spotlight or find "Terminal" in Launchpad).
2. Enter "git". If prompted to install XCode, let it install.
3. Install Homebrew. You can refer to https://brew.sh for more information.
Copy and paste the following:
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
Enter your computer password and press enter.
4. After the installation is complete, copy and paste the following:
(echo; echo 'eval "$(/usr/local/bin/brew shellenv)"')>>/Users/APPLE/.profile
/usr/local/bin/brew shellenv"
5. Install curl and ffmpeg using Homebrew. This may take several minutes.
6. Since brew install takes some time, you can right-click on the Terminal below and select "New Window" to proceed with the following actions.
7. Clone the Whisper.cpp repository: git clone https://github.com/ggerganov/whisper.cpp
8. Change directory to whisper.cpp: cd whisper.cpp
9. Make the medium model: make medium
Download the medium model.
10. Make the large model: make large
Download the large model.
11. To use in the future:
Open the terminal: open .
This command will display the current location as a folder or open Finder and select "Go" => [your personal folder].
Convert the target video file to a pure audio wave file:
ffmpeg -i {input-file} -ar 16000 -ac 1 -c:a pcm_s16le output.wav
Convert output.wav to a transcript using the medium model and save it to output.txt:
./whisper.cpp/main -m ./whisper.cpp/models/ggml-medium.bin -l zh output.wav > output.txt
If you are willing to wait longer, replace "ggml-medium" with "ggml-large" for a more accurate result, although it will take more time.
If the input is not in Chinese, change -l zh to -l auto for automatic language detection.
If you want to output to a different file, replace "output.txt" with the desired filename.
To output as SRT, add "--output-srt" after the command, placed to the left of ">".
Example: ./whisper.cpp/main -m ./whisper.cpp/models/ggml-medium.bin -l zh output.wav --output-srt > output.txt