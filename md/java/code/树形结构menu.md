```java
@Override  
public List<MenuVO> getTreeList() {  
    List<Menu> list = this.list();  
    List<MenuVO> menus = list.stream().map(v -> {  
        MenuVO menu = new MenuVO();  
        BeanUtils.copyProperties(v, menu);  
        return menu;  
    }).collect(Collectors.toList());  
    return menus.stream().filter(v -> v.getParent() == null || v.getParent() == 0)  
            .peek(v -> v.setChildList(getChildList(v, menus))).collect(Collectors.toList());  
}  
  
private List<MenuVO> getChildList(MenuVO menu, List<MenuVO> menus) {  
	return menus.stream().filter(v -> Objects.equals(v.getParent(), menu.getId())).peek(v -> v.setChildList(getChildList(v, menus))).collect(Collectors.toList());  
}
```