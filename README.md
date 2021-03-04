## picgo-plugin-s3

![github-action](https://github.com/wayjam/picgo-plugin-s3/workflows/publish/badge.svg)
![license](https://img.shields.io/github/license/wayjam/picgo-plugin-s3)
[![npm](https://img.shields.io/npm/v/picgo-plugin-s3?style=flat)](https://www.npmjs.com/package/picgo-plugin-s3)

[PicGo](https://github.com/PicGo/PicGo-Core) Amazon S3 上传插件。

- 支持 Amazon S3 与其他如 backblaze b2 等兼容 S3 API 的云存储
- 支持 PicGO GUI

### 安装 Installation

GUI 直接搜索 _S3_ 下载即可，Core 版执行 `picgo add s3` 安装。

### 配置 Configuration

```sh
picgo set uploader aws-s3
```

| Key               | 说明                          | 例子                               |
| ----------------- | ----------------------------- | ---------------------------------- |
| `accessKeyID`     | AWS 凭证 ID                   |                                    |
| `secretAccessKey` | AWS 凭证密钥                  |                                    |
| `bucketName`      | S3 桶名称                     | `gallery`                          |
| `uploadPath`      | 上传路径                      | `{year}/{month}/{fullName}`        |
| `urlPrefix`       | 最终生成图片 URL 的自定义前缀 | `https://img.example.com/my-blog/` |
| `endpoint`        | 指定自定义终端节点            | `s3.us-west-2.amazonaws.com`       |
| `region`          | 指定执行服务请求的区域        | `us-west-1`                        |
| `pathStyleAccess` | 是否启用 S3 Path style | 默认为 `false`，使用 minio 请设置为 `true` |
| `acl` | 访问控制列表，上传资源的访问策略 | 默认为 `public-read` |

**上传路径支持 payload：**

| payload      | 描述                   |
| ------------ | ---------------------- |
| `{year}`     | 当前日期 - 年          |
| `{month}`    | 当前日期 - 月          |
| `{day}`      | 当前日期 - 日          |
| `{fullName}` | 完整文件名（含扩展名） |
| `{fileName}` | 文件名（不含扩展名）   |
| `{extName}`  | 扩展名（不含`.`）      |
| `{md5}`      | 图片 MD5 计算值        |
| `{sha1}`     | 图片 SHA1 计算值       |
| `{sha256}`   | 图片 SHA256 计算值     |

### 示例 Example

```json
    "aws-s3": {
      "accessKeyID": "xxx",
      "secretAccessKey": "xxxxx",
      "bucketName": "my-bucket",
      "uploadPath": "{year}/{md5}.{extName}",
      "endpoint": "s3.us-west-000.backblazeb2.com",
      "urlPrefix": "https://img.example.com/"
    }
```

如果 PicGo 像以上配置，执行上传：`picgo upload sample.png`，则最终得到图片地址为：`https://img.example.com/2021/4aa4f41e38817e5fd38ac870f40dbc70.jpg`

## 贡献 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## 许可证 License

Released under the [MIT License](https://github.com/wayjam/picgo-plugin-s3/blob/master/LICENSE).
