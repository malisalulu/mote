1.npm init
2.修改package.json文件,包管理器限制

```json
 "private": true, // 私有包，只能在当前项目中使用
  "scripts": {
    "preinstall": "npx only-allow pnpm",  
  },
```
3.手动添加pnpm-workspace.yaml文件

```yaml
packages:
  - 'packages/*'
```

4.创建packages文件夹，并在其中创建子文件夹，如：

```
packages
├── package1
│   ├── src
│   │   └── index.ts
│   └── package.json
├── package2
│   ├── src
│   │   └── index.ts
│   └── package.json
└── package3
    ├── src
    │   └── index.ts
    └── package.json
```
5.修改子包的package.json文件

```json
"publishConfig": {
    "access": "public"
  },
```
子包名名字：@mote/test-share @mote/test
6.在test目录下执行：
```bash
pnpm -F @mote/test add @mote/test-share
pnpm i @mote/test-share --filter test

```
7.登陆npm
```bash
npm login
```

8.安装包依赖,根目录下执行：
```bash
pnpm install changeset/cli -w --save-dev
pnpm changeset init
```
![alt text](image.png)

