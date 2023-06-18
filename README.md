# 基础功能模块是发展性测评系统的核心模块，提供了对学生进行评价和记录的基本功能。用户可以方便地添加和管理学生信息，记录学生成长历程并评价学生的行为和表现，以便更好地了解学生的发展情况。

# This basic functional module is the core module of the developmental assessment system, providing the basic functions for evaluating and recording students. Users can easily add and manage student information, record student growth, and evaluate student behavior and performance to better understand student development.

## 以下是Java代码示例：

## Here is a Java code example:

package com.ruoyi.system.domain;

import org.apache.commons.lang3.builder.ToStringBuilder;

import org.apache.commons.lang3.builder.ToStringStyle;

import java.util.Date;

import com.ruoyi.common.annotation.Excel;

import com.ruoyi.common.annotation.Excel.ColumnType;

import com.ruoyi.common.core.domain.BaseEntity;

/**
 * 系统访问记录表 sys_logininfor
 * 
 * @author ruoyi
 */
public class SysLogininfor extends BaseEntity
{
    private static final long serialVersionUID = 1L;

    /** ID */
    @Excel(name = "序号", cellType = ColumnType.NUMERIC)
    private Long infoId;

    /** 用户账号 */
    @Excel(name = "用户账号")
    private String loginName;

    /** 登录状态 0成功 1失败 */
    @Excel(name = "登录状态", readConverterExp = "0=成功,1=失败")
    private String status;

    /** 登录IP地址 */
    @Excel(name = "登录地址")
    private String ipaddr;

    /** 登录地点 */
    @Excel(name = "登录地点")
    private String loginLocation;

    /** 浏览器类型 */
    @Excel(name = "浏览器")
    private String browser;

    /** 操作系统 */
    @Excel(name = "操作系统")
    private String os;

    /** 提示消息 */
    @Excel(name = "提示消息")
    private String msg;

    /** 访问时间 */
    @Excel(name = "访问时间", width = 30, dateFormat = "yyyy-MM-dd HH:mm:ss")
    private Date loginTime;

    public Long getInfoId()
    {
        return infoId;
    }

    public void setInfoId(Long infoId)
    {
        this.infoId = infoId;
    }

    public String getLoginName()
    {
        return loginName;
    }

    public void setLoginName(String loginName)
    {
        this.loginName = loginName;
    }

    public String getStatus()
    {
        return status;
    }

    public void setStatus(String status)
    {
        this.status = status;
    }

    public String getIpaddr()
    {
        return ipaddr;
    }

    public void setIpaddr(String ipaddr)
    {
        this.ipaddr = ipaddr;
    }

    public String getLoginLocation()
    {
        return loginLocation;
    }

    public void setLoginLocation(String loginLocation)
    {
        this.loginLocation = loginLocation;
    }

    public String getBrowser()
    {
        return browser;
    }

    public void setBrowser(String browser)
    {
        this.browser = browser;
    }

    public String getOs()
    {
        return os;
    }

    public void setOs(String os)
    {
        this.os = os;
    }

    public String getMsg()
    {
        return msg;
    }

    public void setMsg(String msg)
    {
        this.msg = msg;
    }

    public Date getLoginTime()
    {
        return loginTime;
    }

    public void setLoginTime(Date loginTime)
    {
        this.loginTime = loginTime;
    }

    @Override
    public String toString() {
    
        return new ToStringBuilder(this,ToStringStyle.MULTI_LINE_STYLE)
        
            .append("infoId", getInfoId())
            
            .append("loginName", getLoginName())
            
            .append("ipaddr", getIpaddr())
            
            .append("loginLocation", getLoginLocation())
            
            .append("browser", getBrowser())
            
            .append("os", getOs())
            
            .append("status", getStatus())
            
            .append("msg", getMsg())
            
            .append("loginTime", getLoginTime())
            
            .toString();
    }
}


# <body>
  <header>
    <div class="logo">My Github Page</div>
    <nav>
      <a href="#">Home</a>
      <a href="#">About</a>
      <a href="#">Contact</a>
    </nav>
  </header>
  <h1>Welcome to My Github Page</h1>
  <footer>&copy; 2023 My Github Page. All rights reserved.</footer>
</body>
</html>
