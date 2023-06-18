# 基础功能模块是发展性测评系统的核心模块，提供了对学生进行评价和记录的基本功能。用户可以方便地添加和管理学生信息，记录学生成长历程并评价学生的行为和表现，以便更好地了解学生的发展情况。

# This basic functional module is the core module of the developmental assessment system, providing the basic functions for evaluating and recording students. Users can easily add and manage student information, record student growth, and evaluate student behavior and performance to better understand student development.

## 以下是Java代码示例：

## Here is a Java code example:

package com.ruoyi.kx.controller;

import com.ruoyi.common.annotation.Log;

import com.ruoyi.common.core.controller.BaseController;

import com.ruoyi.common.core.domain.AjaxResult;

import com.ruoyi.common.core.page.TableDataInfo;

import com.ruoyi.common.enums.BusinessType;

import com.ruoyi.common.utils.poi.ExcelUtil;

import com.ruoyi.kx.bean.KxClassesAllotBean;

import com.ruoyi.kx.domain.KxClasses;

import com.ruoyi.kx.domain.KxClassesAllot;

import com.ruoyi.kx.domain.KxTeacher;

import com.ruoyi.kx.mapper.KxClassesMapper;

import com.ruoyi.kx.mapper.KxTeacherMapper;

import com.ruoyi.kx.service.IKxClassesAllotService;

import com.ruoyi.system.domain.SysUserRole;

import com.ruoyi.system.mapper.SysUserRoleMapper;

import org.springframework.beans.factory.annotation.Autowired;

import org.springframework.stereotype.Controller;

import org.springframework.ui.ModelMap;

import org.springframework.web.bind.annotation.*;

import org.springframework.web.multipart.MultipartFile;


import java.util.ArrayList;

import java.util.List;


/**
 * 学科分配Controller
 *
 * @author huang
 * {@code @date} 2023-02-10
 */
@Controller

@RequestMapping("/kx/ClassAllot")

public class KxClassesAllotController extends BaseController {

    private final String prefix = "kx/ClassAllot";
    
    @Autowired
    
    KxClassesMapper kxClassesMapper;
    
    @Autowired
    
    KxTeacherMapper kxTeacherMapper;
    
    @Autowired
    
    private IKxClassesAllotService kxClassesAllotService;

    //@RequiresPermissions("kx:ClassAllot:view")
    
    @GetMapping()
    
    public String ClassAllot(ModelMap modelMap) {
    
        modelMap.put("loginName", getSysUser().getLoginName());
        
        List<KxClasses> kxClasses = kxClassesMapper.selectKxClassesList(null);
        
        
        List<KxTeacher> kxTeachers = kxTeacherMapper.selectKxTeacherList(null);
        kxClasses = kxClasses.subList(1, kxClasses.size());
        

        List<SysUserRole> sysUserRoles = sysUserRoleMapper.selectUserRoleByUserId(getUserId());
        
        boolean flag = false;
        
        for (SysUserRole sysUserRole : sysUserRoles) {
        
            Long roleId = sysUserRole.getRoleId();
            
            if (roleId == 5) {
            
                flag = true;
                
                break;
                
            }
        }
        modelMap.put("flag", flag);
        
        if (!getSysUser().getLoginName().equals("admin") && !flag) {
        
            KxTeacher kxTeacher = kxTeacherMapper.selectKxTeacherByUserId(getUserId());
            
            kxClasses = new ArrayList<>();
            
            kxClasses.add(kxClassesMapper.selectKxClassesByTeacherId(kxTeacher.getId()));
            
        }

        modelMap.put("classes", kxClasses);
        
        modelMap.put("teacher", kxTeachers);
        
        return prefix + "/ClassAllot";
    }

    @Autowired
    SysUserRoleMapper sysUserRoleMapper;

    /**
     * 查询学科分配列表
     */
    //@RequiresPermissions("kx:ClassAllot:list")
    @PostMapping("/list")
    @ResponseBody
    public TableDataInfo list(KxClassesAllot kxClassesAllot) {
        startPage();
        List<KxClassesAllot> list = kxClassesAllotService.selectKxClassesAllotList(kxClassesAllot);
        return getDataTable(list);
    }

    /**
     * 导出学科分配列表
     */
    //@RequiresPermissions("kx:ClassAllot:export")
    @Log(title = "学科分配", businessType = BusinessType.EXPORT)
    @PostMapping("/export")
    @ResponseBody
    public AjaxResult export(KxClassesAllot kxClassesAllot) {
        List<KxClassesAllot> list = kxClassesAllotService.selectKxClassesAllotList(kxClassesAllot);
        ExcelUtil<KxClassesAllot> util = new ExcelUtil<KxClassesAllot>(KxClassesAllot.class);
        return util.exportExcel(list, "学科分配数据");
    }

    @Log(title = "学科分配", businessType = BusinessType.IMPORT)
    //@RequiresPermissions("kx:ClassAllot:import")
    @PostMapping("/importData")
    @ResponseBody
    public AjaxResult importData(MultipartFile file, boolean updateSupport) throws Exception {
        ExcelUtil<KxClassesAllotBean> util = new ExcelUtil<KxClassesAllotBean>(KxClassesAllotBean.class);
        List<KxClassesAllotBean> kxClassesAllotList = util.importExcel(file.getInputStream());
        String message = kxClassesAllotService.importKxClassesAllot(kxClassesAllotList, updateSupport, getLoginName());
        return AjaxResult.success(message);
    }

    //@RequiresPermissions("kx:ClassAllot:view")
    @GetMapping("/importTemplate")
    @ResponseBody
    public AjaxResult importTemplate() {
        ExcelUtil<KxClassesAllotBean> util = new ExcelUtil<>(KxClassesAllotBean.class);

        return util.importTemplateExcel(" 学科分配数据");
    }

    /**
     * 新增学科分配
     */
    @GetMapping("/add")
    public String add(ModelMap modelMap) {
        modelMap.put("loginName", getSysUser().getLoginName());
        List<KxClasses> kxClasses = kxClassesMapper.selectKxClassesList(null);
        kxClasses = kxClasses.subList(1, kxClasses.size());

        List<SysUserRole> sysUserRoles = sysUserRoleMapper.selectUserRoleByUserId(getUserId());
        boolean flag = false;
        for (SysUserRole sysUserRole : sysUserRoles) {
            Long roleId = sysUserRole.getRoleId();
            if (roleId == 5) {
                flag = true;
                break;
            }
        }
        modelMap.put("flag", flag);
        if (!flag) {
            KxTeacher kxTeacher = kxTeacherMapper.selectKxTeacherByUserId(getUserId());
            kxClasses = new ArrayList<>();
            kxClasses.add(kxClassesMapper.selectKxClassesByTeacherId(kxTeacher.getId()));
        }

        modelMap.put("classes", kxClasses);
        modelMap.put("teacher", kxTeacherMapper.selectKxTeacherList(null));
        return prefix + "/add";
    }

    /**
     * 新增保存学科分配
     */
    //@RequiresPermissions("kx:ClassAllot:add")
    @Log(title = "学科分配", businessType = BusinessType.INSERT)
    @PostMapping("/add")
    @ResponseBody
    public AjaxResult addSave(KxClassesAllot kxClassesAllot) {
        KxTeacher teacher = kxTeacherMapper.selectKxTeacherById(kxClassesAllot.getTeacherId());
        sysUserRoleMapper.insertUserAndRole(teacher.getUserId(), 6L);
        return toAjax(kxClassesAllotService.insertKxClassesAllot(kxClassesAllot));
    }

    /**
     * 修改学科分配
     */

    //@RequiresPermissions("kx:ClassAllot:edit")
    @GetMapping("/edit/{id}")
    public String edit(@PathVariable("id") Long id, ModelMap modelMap) {
        KxClassesAllot kxClassesAllot = kxClassesAllotService.selectKxClassesAllotById(id);
        modelMap.put("kxClassesAllot", kxClassesAllot);
        modelMap.put("loginName", getSysUser().getLoginName());
        List<KxClasses> kxClasses = kxClassesMapper.selectKxClassesList(null);
        kxClasses = kxClasses.subList(1, kxClasses.size());

        List<SysUserRole> sysUserRoles = sysUserRoleMapper.selectUserRoleByUserId(getUserId());

        boolean flag = false;

        for (SysUserRole sysUserRole : sysUserRoles) {
            Long roleId = sysUserRole.getRoleId();
            if (roleId == 5) {
                flag = true;
                break;
            }
        }
        modelMap.put("flag", flag);
        if (!flag) {
            KxTeacher kxTeacher = kxTeacherMapper.selectKxTeacherByUserId(getUserId());
            kxClasses = new ArrayList<>();
            kxClasses.add(kxClassesMapper.selectKxClassesByTeacherId(kxTeacher.getId()));
        }

        modelMap.put("classes", kxClasses);
        modelMap.put("teacher", kxTeacherMapper.selectKxTeacherList(null));
        return prefix + "/edit";
    }

    /**
     * 修改保存学科分配
     */
    //@RequiresPermissions("kx:ClassAllot:edit")
    @Log(title = "学科分配", businessType = BusinessType.UPDATE)
    @PostMapping("/edit")
    @ResponseBody
    public AjaxResult editSave(KxClassesAllot kxClassesAllot) {
        KxTeacher teacher = kxTeacherMapper.selectKxTeacherById(kxClassesAllot.getTeacherId());
        sysUserRoleMapper.insertUserAndRole(teacher.getUserId(), 6L);
        return toAjax(kxClassesAllotService.updateKxClassesAllot(kxClassesAllot));
    }

    /**
     * 删除学科分配
     */
    //@RequiresPermissions("kx:ClassAllot:remove")
    @Log(title = "学科分配", businessType = BusinessType.DELETE)
    @PostMapping("/remove")
    @ResponseBody
    public AjaxResult remove(String ids) {
        String[] str = ids.split(",");
        for (String s : str) {
            KxClassesAllot kxClassesAllot = kxClassesAllotService.selectKxClassesAllotById(Long.valueOf(s));
            KxTeacher teacher = kxTeacherMapper.selectKxTeacherById(kxClassesAllot.getTeacherId());
            sysUserRoleMapper.deleteUserRoleByUserIdAndRoleId(teacher.getUserId(), 6L);
        }
        return toAjax(kxClassesAllotService.deleteKxClassesAllotByIds(ids));
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
