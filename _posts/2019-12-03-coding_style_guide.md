---
title: Coding Stype guide 
author: daniel.choi
layout: post
---

## Coding Stype guide 

* 제어문(Control Statement)  
  * if *case 1*
  ``` java
  public boolean isModel(Integer i) {

        : logic 1

      if( i == null) {
          return false;
      } else {

          : logic 2 
          return true;
      }
  }
  ```

  * if *case 2*
  ``` java
  public boolean isModel(Integer i) {
    
      if( i == null) {
          return false;
      }

        : logic 1
        : logic 2
      return true;
  }
  ```
* 메소드 (Method) 
  * if *case 1*
    ``` java
    public void method() {
        for(Model model : ModelList) {
            : 
        }
    }
    ```` 
  * if *case 2*
    ``` java *case 2*
    public void method() {
        for(Model model : ModelList) {
            method2(model);
        }
    }
    private void method2(Model model) {
        :
    }
    ```` 
