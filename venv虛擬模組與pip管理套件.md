python -m venv tutorial-env /建立
source tutorial-env/bin/activate /MAC啟動
（這段程式碼適用於 bash shell。如果你是用 csh 或者 fish shell，應當使用替代的 activate.csh 與 activate.fish 腳本。）

啟動虛擬環境會改變你的 shell 提示字元來顯示你正在使用的虛擬環境，並且修改環境以讓你在執行 python 的時候可以得到特定的 Python 版本，例如：

$ source ~/envs/tutorial-env/bin/activate
(tutorial-env) $ python
Python 3.5.1 (default, May  6 2016, 10:59:36)
  ...
>>> import sys
>>> sys.path
['', '/usr/local/lib/python35.zip', ...,
'~/envs/tutorial-env/lib/python3.5/site-packages']
>>>

要停用虛擬環境，輸入：deactivate


用 pip 管理套件
你可以使用一個叫做 pip 的程式來安裝、升級和移除套件。pip 預設會從 Python Package Index 安裝套件。你可以透過你的網頁瀏覽器瀏覽 Python Package Index。

pip 有好幾個子指令："install"、"uninstall"、"freeze" 等等。（可以參考安裝 Python 模組指南，來取得 pip 的完整說明文件。）

你可以透過指定套件名字來安裝最新版本的套件：

(tutorial-env) $ python -m pip install novas
Collecting novas
  Downloading novas-3.1.1.3.tar.gz (136kB)
Installing collected packages: novas
  Running setup.py install for novas
Successfully installed novas-3.1.1.3
你也可以透過在套件名稱之後接上 == 和版號來指定特定版本：

(tutorial-env) $ python -m pip install requests==2.6.0
Collecting requests==2.6.0
  Using cached requests-2.6.0-py2.py3-none-any.whl
Installing collected packages: requests
Successfully installed requests-2.6.0
要是你重新執行此指令，pip 會知道該版本已經安裝過，然後什麼也不做。你可以提供不同的版本號碼來取得該版本，或是可以執行 python -m pip install --upgrade 來把套件升級到最新的版本：

(tutorial-env) $ python -m pip install --upgrade requests
Collecting requests
Installing collected packages: requests
  Found existing installation: requests 2.6.0
    Uninstalling requests-2.6.0:
      Successfully uninstalled requests-2.6.0
Successfully installed requests-2.7.0
python -m pip uninstall 後面接一個或是多個套件名稱可以從虛擬環境中移除套件。

python -m pip show 可以顯示一個特定套件的資訊：

(tutorial-env) $ python -m pip show requests
---
Metadata-Version: 2.0
Name: requests
Version: 2.7.0
Summary: Python HTTP for Humans.
Home-page: http://python-requests.org
Author: Kenneth Reitz
Author-email: me@kennethreitz.com
License: Apache 2.0
Location: /Users/akuchling/envs/tutorial-env/lib/python3.4/site-packages
Requires:
python -m pip list 會顯示虛擬環境中所有已經安裝的套件：

(tutorial-env) $ python -m pip list
novas (3.1.1.3)
numpy (1.9.2)
pip (7.0.3)
requests (2.7.0)
setuptools (16.0)
python -m pip freeze 可以複製一整個已經安裝的套件清單，但是輸出使用 python -m pip install 可以讀懂的格式。一個常見的慣例是放這整個清單到一個叫做 requirements.txt 的檔案：

(tutorial-env) $ python -m pip freeze > requirements.txt
(tutorial-env) $ cat requirements.txt
novas==3.1.1.3
numpy==1.9.2
requests==2.7.0
requirements.txt 可以提交到版本控制，並且作為釋出應用程式的一部分。使用者可以透過 install -r 安裝對應的的套件：

(tutorial-env) $ python -m pip install -r requirements.txt
Collecting novas==3.1.1.3 (from -r requirements.txt (line 1))
  ...
Collecting numpy==1.9.2 (from -r requirements.txt (line 2))
  ...
Collecting requests==2.7.0 (from -r requirements.txt (line 3))
  ...
Installing collected packages: novas, numpy, requests
  Running setup.py install for novas
Successfully installed novas-3.1.1.3 numpy-1.9.2 requests-2.7.0
