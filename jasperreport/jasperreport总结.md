
# <center> jasperreport总结 </center>
## 杂
### JavaWeb报表优劣
- JasperReport  
  开源、文档付费、jasper studio基于Eclipse
- Birt  
  基于Eclipse、功能不够
- FineReport  
  收费、简单、漂亮

## 操作步骤

### 概括
- 用jasper studio编辑.jrxml文件文件生成.jasper文件（报表模板）
- 将.jasper模板加入项目工程中，通过jasperreport提供的库类填充报表，输出到浏览器或导出  

### 具体
#### jasper studio绘制报表
1. 安装jasper studio  
    界面比ireport简洁大方
![](安装.png)
- 新建工程  
    基于Eclipse，所以跟Eclipse一样
![](新建工程.png)
- 添加jar包  
    若是在Eclipse的项目中，需要添加以下jar包：  
      jasperreport
      itext
      itext-Asian
    而jasper studio中自带jasperreport包  
    ![](jasperreport包.png)  
    只需添加另外2个  
    ![](添加jar包.png)  

- 新建模板  
![](新建模板.png)
- 添加数据源  
![](添加数据源.png)
