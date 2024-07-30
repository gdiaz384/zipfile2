## zipfile2

Python utility to unpack archive.zip files.

Features:
- Cross platform (Windows, Linux).
- CLI interface.
- Supports file and folder name encodings like shift-jis, cp932, gbk from zip files.
- Has encoding autodetection code based upon charamel library to increase success rate and provide hints.
- Supports archives with passwords.
- Supports batch extracting with `*`.
- Archives with multiple items are extracted to subfolders automatically.
- Archives are always extracted relative to the target.

Core logic is from Python 3.11 standard library + a few updates for the features above.

### Usage:

- version = 2024.07.30
- In the commands below, Linux users should use `python3` if `python` does not work.

```
python zipfile2.py --help
python zipfile2.py --h
python zipfile2.py archive.zip --list
python zipfile2.py archive.zip -l
python zipfile2.py archive.zip --encoding shift-jis
python zipfile2.py archive.zip - shift-jis
python zipfile2.py archive.zip
python zipfile2.py *
```

### Dependencies and Notes:

- At least Python 3.4+ due to pathlib dependency, but likely Python 3.6+. Was developed on Python 3.10.
- If the charamel library is available, it is used to detect character encoding.
    - To use charamel, it must be installed with: pip install charamel
    - charamel requires Python 3.6+
- To compile zipfle2 into a platform specific executable, use pyinstaller.
- List of encodings: https://docs.python.org/3/library/codecs.html#standard-encodings

### To compile:

- Install Python.
    - Version 3.8+ is recommended but 3.6+ might work.
    - Windows 7 users should use [this repository](//github.com/adang1345/PythonWin7).
- Download the `zipfile2.py` file.
- Open a command prompt, `cmd.exe`, or terminal.

```
python --version # Must be 3.6+
python -m pip install pyinstaller
python -m PyInstaller --version # Make sure this is installed. Case sensitive.
# charamel is not required but helps detect encodings if it is available.
python -m pip install charamel
python -m PyInstaller --onefile path\to\zipfile2.py
```

- Look for the output under `dist/*`.
- Linux users should use `python3`.
- See **Usage** for usage instructions.

### License:

- The majority of zipfle2.py is under Python's standard license.
- Changes are licensed under [Apache 2.0](LICENSE).
- charamel is Apache 2.0 https://pypi.org/project/charamel
