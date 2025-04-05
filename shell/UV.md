以下是 UV 命令行工具的表格形式参考文档：

---

### **UV 命令参考表**

| **命令**                 | **功能**       | **常用参数**                                                                           | **示例**                                                                   |
| ---------------------- | ------------ | ---------------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| **`uv pip install`**   | 安装 Python 包  | `-r <file>`：从需求文件安装<br>`--no-deps`：不安装依赖<br>`--index-url <url>`：自定义索引源<br>`-U`：升级包 | `uv pip install flask`<br>`uv pip install -r requirements.txt`           |
| **`uv pip uninstall`** | 卸载包          | `-r <file>`：从需求文件卸载<br>`-y`：跳过确认                                                   | `uv pip uninstall flask -y`                                              |
| **`uv pip freeze`**    | 输出已安装包列表     | `--all`：包含系统工具包<br>`--exclude-editable`：排除可编辑包                                     | `uv pip freeze > requirements.txt`                                       |
| **`uv pip list`**      | 列出已安装包       | `--outdated`：显示过时包<br>`--format json`：JSON 格式输出                                    | `uv pip list --outdated`                                                 |
| **`uv pip show`**      | 显示包详情        | 无                                                                                  | `uv pip show flask`                                                      |
| **`uv pip check`**     | 检查依赖冲突       | 无                                                                                  | `uv pip check`                                                           |
| **`uv pip sync`**      | 同步虚拟环境       | `--reinstall`：强制重新安装<br>`--system`：安装到系统 Python                                    | `uv pip sync requirements.txt`                                           |
| **`uv pip compile`**   | 编译需求文件       | `--upgrade`：升级所有依赖<br>`--generate-hashes`：生成哈希                                     | `uv pip compile requirements.in`                                         |
| **`uv venv`**          | 创建虚拟环境       | `--python <path>`：指定解释器<br>`--no-seed`：不安装种子包                                      | `uv venv .venv --python=3.10`<br># 指定环境保存目录<br>uv venv /path/to/venv<br> |
| **`uv run`**           | 运行 Python 应用 | `--reload`：开发热重载<br>`--port <num>`：指定端口                                            | `uv run app:main --reload`                                               |

---

### **全局参数表**
| **参数**              | **说明** | **示例**                                     |
| ------------------- | ------ | ------------------------------------------ |
| `--cache-dir <dir>` | 指定缓存目录 | `uv pip install flask --cache-dir ./cache` |
| `--no-cache-dir`    | 禁用缓存   | `uv pip install --no-cache-dir`            |
| `--quiet`           | 静默模式   | `uv pip install --quiet`                   |
| `--verbose`         | 详细输出   | `uv pip install --verbose`                 |

---

### **环境变量表**
| **变量名**        | **作用**        | **示例值**                                       |
| -------------- | ------------- | --------------------------------------------- |
| `UV_INDEX_URL` | 默认包索引源        | `export UV_INDEX_URL=https://pypi.org/simple` |
| `UV_CACHE_DIR` | 缓存目录          | `export UV_CACHE_DIR=./uv_cache`              |
| `UV_PYTHON`    | 指定 Python 解释器 | `export UV_PYTHON=/usr/bin/python3.11`        |

---

### **常用场景示例**
1. **创建并激活虚拟环境**  
   ```bash
   uv venv .venv
   source .venv/bin/activate  # Linux/macOS
   ```

2. **从 `requirements.in` 生成锁定文件**  
   ```bash
   uv pip compile requirements.in --output-file requirements.txt
   ```

3. **生产环境同步依赖**  
   ```bash
   uv pip sync requirements.txt --strict
   ```

4. **开发模式运行应用**  
   ```bash
   uv run main:app --reload --port 8000
   ```

---

此表格可作为快速参考，更多细节可通过 `uv <command> --help` 查看。