C:\Users\user\PycharmProjects\pythonProject\.venv\Scripts\python.exe "C:/Program Files/JetBrains/PyCharm Community Edition 2023.3.2/plugins/python-ce/helpers/pycharm/_jb_pytest_runner.py" --target app.py::test_dataset 
Testing started at 12:18 ...
Launching pytest with arguments app.py::test_dataset --no-header --no-summary -q in C:\Users\user\PycharmProjects\pythonProject

============================= test session starts =============================
collecting ... Windows fatal exception: access violation

Current thread 0x00002170 (most recent call first):
  File "<frozen importlib._bootstrap>", line 488 in _call_with_frames_removed
  File "<frozen importlib._bootstrap_external>", line 1317 in create_module
  File "<frozen importlib._bootstrap>", line 813 in module_from_spec
  File "<frozen importlib._bootstrap>", line 921 in _load_unlocked
  File "<frozen importlib._bootstrap>", line 1331 in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 1360 in _find_and_load
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\tensorflow\python\pywrap_tensorflow.py", line 74 in <module>
  File "<frozen importlib._bootstrap>", line 488 in _call_with_frames_removed
  File "<frozen importlib._bootstrap_external>", line 1023 in exec_module
  File "<frozen importlib._bootstrap>", line 935 in _load_unlocked
  File "<frozen importlib._bootstrap>", line 1331 in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 1360 in _find_and_load
  File "<frozen importlib._bootstrap>", line 488 in _call_with_frames_removed
  File "<frozen importlib._bootstrap>", line 1415 in _handle_fromlist
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\tensorflow\__init__.py", line 40 in <module>
  File "<frozen importlib._bootstrap>", line 488 in _call_with_frames_removed
  File "<frozen importlib._bootstrap_external>", line 1023 in exec_module
  File "<frozen importlib._bootstrap>", line 935 in _load_unlocked
  File "<frozen importlib._bootstrap>", line 1331 in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 1360 in _find_and_load
  File "C:\Users\user\PycharmProjects\pythonProject\app.py", line 3 in <module>
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\assertion\rewrite.py", line 197 in exec_module
  File "<frozen importlib._bootstrap>", line 935 in _load_unlocked
  File "<frozen importlib._bootstrap>", line 1331 in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 1360 in _find_and_load
  File "<frozen importlib._bootstrap>", line 1387 in _gcd_import
  File "C:\Users\user\AppData\Local\Programs\Python\Python313\Lib\importlib\__init__.py", line 88 in import_module
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\pathlib.py", line 587 in import_path
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 507 in importtestmodule
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 560 in _getobj
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 289 in obj
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 576 in _register_setup_module_fixture
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 563 in collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 398 in collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 353 in from_call
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 400 in pytest_make_collect_report
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_callers.py", line 121 in _multicall
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_manager.py", line 120 in _hookexec
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_hooks.py", line 512 in __call__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 576 in collect_one_node
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 883 in _collect_one_node
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 961 in collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 398 in collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 353 in from_call
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 400 in pytest_make_collect_report
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_callers.py", line 121 in _multicall
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_manager.py", line 120 in _hookexec
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_hooks.py", line 512 in __call__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 576 in collect_one_node
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 837 in perform_collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 382 in pytest_collection
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_callers.py", line 121 in _multicall
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_manager.py", line 120 in _hookexec
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_hooks.py", line 512 in __call__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 371 in _main
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 318 in wrap_session
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 365 in pytest_cmdline_main
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_callers.py", line 121 in _multicall
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_manager.py", line 120 in _hookexec
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_hooks.py", line 512 in __call__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\config\__init__.py", line 199 in main
  File "C:\Program Files\JetBrains\PyCharm Community Edition 2023.3.2\plugins\python-ce\helpers\pycharm\_jb_pytest_runner.py", line 60 in <module>
Windows fatal exception: access violation

Current thread 0x00002170 (most recent call first):
  File "C:\Users\user\AppData\Local\Programs\Python\Python313\Lib\ctypes\__init__.py", line 379 in _load_library
  File "C:\Users\user\AppData\Local\Programs\Python\Python313\Lib\ctypes\__init__.py", line 361 in __init__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\tensorflow\python\platform\windows_lib_diagnostics.py", line 156 in diagnose_dll_load
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\tensorflow\python\platform\windows_lib_diagnostics.py", line 206 in run_diagnosis
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\tensorflow\python\pywrap_tensorflow.py", line 92 in <module>
  File "<frozen importlib._bootstrap>", line 488 in _call_with_frames_removed
  File "<frozen importlib._bootstrap_external>", line 1023 in exec_module
  File "<frozen importlib._bootstrap>", line 935 in _load_unlocked
  File "<frozen importlib._bootstrap>", line 1331 in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 1360 in _find_and_load
  File "<frozen importlib._bootstrap>", line 488 in _call_with_frames_removed
  File "<frozen importlib._bootstrap>", line 1415 in _handle_fromlist
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\tensorflow\__init__.py", line 40 in <module>
  File "<frozen importlib._bootstrap>", line 488 in _call_with_frames_removed
  File "<frozen importlib._bootstrap_external>", line 1023 in exec_module
  File "<frozen importlib._bootstrap>", line 935 in _load_unlocked
  File "<frozen importlib._bootstrap>", line 1331 in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 1360 in _find_and_load
  File "C:\Users\user\PycharmProjects\pythonProject\app.py", line 3 in <module>
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\assertion\rewrite.py", line 197 in exec_module
  File "<frozen importlib._bootstrap>", line 935 in _load_unlocked
  File "<frozen importlib._bootstrap>", line 1331 in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 1360 in _find_and_load
  File "<frozen importlib._bootstrap>", line 1387 in _gcd_import
  File "C:\Users\user\AppData\Local\Programs\Python\Python313\Lib\importlib\__init__.py", line 88 in import_module
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\pathlib.py", line 587 in import_path
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 507 in importtestmodule
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 560 in _getobj
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 289 in obj
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 576 in _register_setup_module_fixture
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\python.py", line 563 in collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 398 in collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 353 in from_call
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 400 in pytest_make_collect_report
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_callers.py", line 121 in _multicall
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_manager.py", line 120 in _hookexec
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_hooks.py", line 512 in __call__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 576 in collect_one_node
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 883 in _collect_one_node
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 961 in collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 398 in collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 353 in from_call
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 400 in pytest_make_collect_report
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_callers.py", line 121 in _multicall
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_manager.py", line 120 in _hookexec
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_hooks.py", line 512 in __call__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\runner.py", line 576 in collect_one_node
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 837 in perform_collect
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 382 in pytest_collection
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_callers.py", line 121 in _multicall
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_manager.py", line 120 in _hookexec
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_hooks.py", line 512 in __call__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 371 in _main
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 318 in wrap_session
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\main.py", line 365 in pytest_cmdline_main
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_callers.py", line 121 in _multicall
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_manager.py", line 120 in _hookexec
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\pluggy\_hooks.py", line 512 in __call__
  File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\_pytest\config\__init__.py", line 199 in main
  File "C:\Program Files\JetBrains\PyCharm Community Edition 2023.3.2\plugins\python-ce\helpers\pycharm\_jb_pytest_runner.py", line 60 in <module>

[TensorFlow DLL Diagnostic] Analyzing: C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\tensorflow\python\_pywrap_tensorflow_internal.pyd
[Error] Failed to load _pywrap_tensorflow_common.dll: INITIALIZATION FAILED (0x45A) - The DLL's DllMain returned false.
    Hint: This often happens if your CPU lacks required instructions (like AVX/AVX2)
    or if the Microsoft Visual C++ Redistributable is outdated/missing.

app.py:None (app.py)
ImportError while importing test module 'C:\Users\user\PycharmProjects\pythonProject\app.py'.
Hint: make sure your test modules/packages have valid Python names.
Traceback:
.venv\Lib\site-packages\tensorflow\python\pywrap_tensorflow.py:74: in <module>
    from tensorflow.python._pywrap_tensorflow_internal import *
E   ImportError: DLL load failed while importing _pywrap_tensorflow_internal: Произошел сбой в программе инициализации библиотеки динамической компоновки (DLL).

The above exception was the direct cause of the following exception:
.venv\Lib\site-packages\_pytest\python.py:507: in importtestmodule
    mod = import_path(
.venv\Lib\site-packages\_pytest\pathlib.py:587: in import_path
    importlib.import_module(module_name)
..\..\AppData\Local\Programs\Python\Python313\Lib\importlib\__init__.py:88: in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
<frozen importlib._bootstrap>:1387: in _gcd_import
    ???
<frozen importlib._bootstrap>:1360: in _find_and_load
    ???
<frozen importlib._bootstrap>:1331: in _find_and_load_unlocked
    ???
<frozen importlib._bootstrap>:935: in _load_unlocked
    ???
.venv\Lib\site-packages\_pytest\assertion\rewrite.py:197: in exec_module
    exec(co, module.__dict__)
app.py:3: in <module>
    import tensorflow as tf
.venv\Lib\site-packages\tensorflow\__init__.py:40: in <module>
    from tensorflow.python import pywrap_tensorflow as _pywrap_tensorflow  # pylint: disable=unused-import
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
.venv\Lib\site-packages\tensorflow\python\pywrap_tensorflow.py:97: in <module>
    raise ImportError(
E   ImportError: Traceback (most recent call last):
E     File "C:\Users\user\PycharmProjects\pythonProject\.venv\Lib\site-packages\tensorflow\python\pywrap_tensorflow.py", line 74, in <module>
E       from tensorflow.python._pywrap_tensorflow_internal import *
E   ImportError: DLL load failed while importing _pywrap_tensorflow_internal: Произошел сбой в программе инициализации библиотеки динамической компоновки (DLL).
E   
E   
E   Failed to load the native TensorFlow runtime.
E   See https://www.tensorflow.org/install/errors for some common causes and solutions.
E   If you need help, create an issue at https://github.com/tensorflow/tensorflow/issues and include the entire stack trace above this error message.
collected 0 items / 1 error

============================== 1 error in 1.86s ===============================
ERROR: found no collectors for C:\Users\user\PycharmProjects\pythonProject\app.py::test_dataset


Process finished with exit code 4
