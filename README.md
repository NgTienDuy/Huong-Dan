# Huong-Dan

Quy trình thực hiện 1 dự án:
Bước 1: Tạo project
  ```bash
  mkdir <Myproject>
  cd <Myproject>
  code .
  ```
Bước 2: Tạo virtual env
  ```bash
  python -m venv .venv
  ```
Bước 3: Activate
  ```bash
  .venv\Scripts\activate
  ```
Bước 4: Cài thư viện
  ```bash
  pip install -r requirements.txt
  ```
Bước 5: Chọn interpreter
Bước 6: 
  ```bash
  claude
  ```
  Tạo claude.md
Bước 7: Cấu hình vscode
  ```.vscode/settings.json
  {
    "python.defaultInterpreterPath": ".venv/bin/python",
    "python.terminal.activateEnvironment": true
  }
  ```
  ```windows
  {
    "python.defaultInterpreterPath": ".venv\\Scripts\\python.exe"
  }
