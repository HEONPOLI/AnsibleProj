# AnsibleProj
# 1. wp_import

requirements :          
ansible >= 2.9          
제어노드에서 관리노드로의 키기반 ssh 인증이 된 상태           

**목적** : ansible playbook의 키워드중 import_tasks 를 이용해 main이 되는 playbook의 하드코딩을 줄인다.        
실행방법 :      
제어노드에서        
1. 해당 레포지토리 clone       
2. AnsibleProj/wp_import 로 디렉토리 이동       
3. playbook 실행
```
ansible-playbook multioswp.yaml -b 
```
---
# 2. wp_using_roles     

requirements:         
ansible >= 2.9        
제어노드에서 관리노드로의 키기반 ssh 인증이 된 상태            

**목적** : ansible의 Artifact 재사용효율의 향상을 위해 roles 키워드를 사용한다.         
실행방법:        
제어노드에서      
1. 해당 레포지토리 clone
2. AnsibleProj/wp_using_roles 디렉토리로 이동
3. playbook 실행
```
ansible-playbook deploy_wordpress_db_roles.yaml -b
```
디렉토리의 구조는 다음과 같다   
```bash
.
├── deploy_wordpress_db_roles.yaml
└── roles
    ├── database
    │   ├── handlers
    │   │   └── main.yaml
    │   ├── tasks
    │   │   └── main.yaml
    │   └── vars
    │       └── main.yaml
    └── wordpress
        ├── handlers
        │   └── main.yaml
        ├── tasks
        │   └── main.yaml
        ├── templates
        │   ├── ports.j2
        │   ├── portsrh.j2
        │   └── wp-config.php.j2
        └── vars
            └── main.yaml
```
database 역할에는 handler, tasks, vars 만 생성하였다.       
wordpress 역할에는 wordpress의 설정파일인 wp-config.php 와 apache2, httpd 서비스의 포트변경을 위해 templates 디렉토리를 생성해주었다.       
