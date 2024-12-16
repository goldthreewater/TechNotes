1. 查看当前仓库的配置信息

   ```
   git config --list
   ```

   

2. 在项目根目录下运行以下命令来设置本地的用户名和邮箱：

   ```bash
   git config user.name "金淼(CV算法架构组)" 
   git config user.email "jinmiao5@yiche.com"
   ```

3. 确认当前的远程仓库URL

   ```
   git remote -v
   ```

4. 添加/切换远程仓库连接的协议

   ```
   git remote add origin ssh://git@gitlab2.bitautotech.com:10001/aivideo/logo_remove.git
   git remote set-url origin http://gitlab2.bitautotech.com/aivideo/logo_remove.git
   ```

   

