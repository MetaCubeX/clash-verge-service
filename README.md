# Clash Verge Service

A Windows Service.



函数包括`get_version`，`start_clash`，`stop_clash`和`get_clash`。通过RESTful API 调用 `port:33211`

---

## GET /version

### 描述

获取服务进程的版本。

### 返回值

返回一个`Result<HashMap<String, String>>`类型的值。如果成功，返回一个包含服务名称和版本的 HashMap。

---

## POST /start_clash

### 描述

启动 clash 进程。

### 参数

接受一个`StartBody`类型的参数，包含以下字段：

- `core_type`: clash 的核心类型，可选，默认为"clash"。
- `config_dir`: 配置目录，必选。
- `config_file`: 配置文件，必选。
- `log_file`: 日志文件，可选。
- `bin_path`: 可执行文件的路径，必选。

### 返回值

返回一个`Result<()>`类型的值。如果成功，返回`Ok(())`。

---

## POST /stop_clash

### 描述

停止 clash 进程。

### 返回值

返回一个`Result<()>`类型的值。如果成功，返回`Ok(())`。如果 clash 没有执行，返回一个错误`bail!("clash not executed")`。

---

## GET /get_clash

### 描述

获取 clash 当前执行信息。

### 返回值

返回一个`Result<StartBody>`类型的值。如果成功，返回`Ok(info)`，其中`info`是 clash 的当前执行信息。如果 clash 没有执行，返回一个错误`bail!("clash not executed")`。

---

