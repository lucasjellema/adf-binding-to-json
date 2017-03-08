# adf-binding-to-json
Example of bean that makes data from data bindings available as nested JSON object in client side JavaScript

To fuel rich client components that live in the browser only (for data visualization for example) it is convenient to be able to make data from the ADF Bindings Layer available in the client - as JavaScript object.

JSON is a easy format to go from server side data through a structured String representation to a native JavaScript data structure.

This project contains a class - JsonProvider - that can be used as managed bean. The bean will produce a JSON string for all data in an iterator binding that is passed into it.



In the JSF page:
```
        <script type="text/javascript">
          /* assign the contents of the collectionModel through a JSON formatted string to the global JS variable deptData */
          var deptData = #{jsonProviderBean[bindings.DeptView2.DCIteratorBinding]};
        </script>
```

Based on the tree binding in the Page Definition file:

```
    <tree IterBinding="DeptView2Iterator" id="DeptView2">
```

(a tree binding for DeptView and nested EmpView , business components against the DEPT and EMP table)

And this entry in adfc-config.xml:
```
<managed-bean id="__1">
    <managed-bean-name>jsonProviderBean</managed-bean-name>
    <managed-bean-class>nl.amis.json.view.JsonProvider</managed-bean-class>
    <managed-bean-scope>request</managed-bean-scope>
  </managed-bean>
```

The resulting JSON string is:


```
{
   "attributes": {
      "Deptno": "java.lang.Integer",
      "Dname": "java.lang.String",
      "Loc": "java.lang.String"
   },
   "values": [
      {
         "Deptno": 10,
         "Dname": "ACCOUNTING",
         "Loc": "NEW YORK",
         "Emps": [
            {
               "Empno": 7782,
               "Ename": "CLARK",
               "Job": "MANAGER",
               "Mgr": 7839,
               "Hiredate": "1981-06-09 00:00:00.0",
               "Sal": 2450,
               "Comm": null,
               "Deptno": 10,
               "Dept": "ViewRow [oracle.jbo.Key[10 ]]"
            },
            {
               "Empno": 7839,
               "Ename": "KING",
               "Job": "PRESIDENT",
               "Mgr": null,
               "Hiredate": "1981-11-17 00:00:00.0",
               "Sal": 5000,
               "Comm": null,
               "Deptno": 10,
               "Dept": "ViewRow [oracle.jbo.Key[10 ]]"
            },
            {
               "Empno": 7934,
               "Ename": "MILLER",
               "Job": "CLERK",
               "Mgr": 7782,
               "Hiredate": "1982-01-23 00:00:00.0",
               "Sal": 1300,
               "Comm": null,
               "Deptno": 10,
               "Dept": "ViewRow [oracle.jbo.Key[10 ]]"
            }
         ]
      },
      {
         "Deptno": 20,
         "Dname": "RESEARCH",
         "Loc": "DALLAS",
         "Emps": [
            {
               "Empno": 7369,
               "Ename": "SMITH",
               "Job": "CLERK",
               "Mgr": 7902,
               "Hiredate": "1980-12-17 00:00:00.0",
               "Sal": 800,
               "Comm": null,
               "Deptno": 20,
               "Dept": "ViewRow [oracle.jbo.Key[20 ]]"
            },
            {
               "Empno": 7566,
               "Ename": "JONES",
               "Job": "MANAGER",
               "Mgr": 7839,
               "Hiredate": "1981-04-02 00:00:00.0",
               "Sal": 2975,
               "Comm": null,
               "Deptno": 20,
               "Dept": "ViewRow [oracle.jbo.Key[20 ]]"
            },
            {
               "Empno": 7788,
               "Ename": "SCOTT",
               "Job": "ANALYST",
               "Mgr": 7566,
               "Hiredate": "1982-12-09 00:00:00.0",
               "Sal": 3000,
               "Comm": null,
               "Deptno": 20,
               "Dept": "ViewRow [oracle.jbo.Key[20 ]]"
            },
            {
               "Empno": 7876,
               "Ename": "ADAMS",
               "Job": "CLERK",
               "Mgr": 7788,
               "Hiredate": "1983-01-12 00:00:00.0",
               "Sal": 1100,
               "Comm": null,
               "Deptno": 20,
               "Dept": "ViewRow [oracle.jbo.Key[20 ]]"
            },
            {
               "Empno": 7902,
               "Ename": "FORD",
               "Job": "ANALYST",
               "Mgr": 7566,
               "Hiredate": "1981-12-03 00:00:00.0",
               "Sal": 3000,
               "Comm": null,
               "Deptno": 20,
               "Dept": "ViewRow [oracle.jbo.Key[20 ]]"
            }
         ]
      },
      {
         "Deptno": 30,
         "Dname": "SALES",
         "Loc": "CHICAGO",
         "Emps": [
            {
               "Empno": 7499,
               "Ename": "ALLEN",
               "Job": "SALESMAN",
               "Mgr": 7698,
               "Hiredate": "1981-02-20 00:00:00.0",
               "Sal": 1600,
               "Comm": 300,
               "Deptno": 30,
               "Dept": "ViewRow [oracle.jbo.Key[30 ]]"
            },
            {
               "Empno": 7521,
               "Ename": "WARD",
               "Job": "SALESMAN",
               "Mgr": 7698,
               "Hiredate": "1981-02-22 00:00:00.0",
               "Sal": 1250,
               "Comm": 500,
               "Deptno": 30,
               "Dept": "ViewRow [oracle.jbo.Key[30 ]]"
            },
            {
               "Empno": 7654,
               "Ename": "MARTIN",
               "Job": "SALESMAN",
               "Mgr": 7698,
               "Hiredate": "1981-09-28 00:00:00.0",
               "Sal": 1250,
               "Comm": 1400,
               "Deptno": 30,
               "Dept": "ViewRow [oracle.jbo.Key[30 ]]"
            },
            {
               "Empno": 7698,
               "Ename": "BLAKE",
               "Job": "MANAGER",
               "Mgr": 7839,
               "Hiredate": "1981-05-01 00:00:00.0",
               "Sal": 2850,
               "Comm": null,
               "Deptno": 30,
               "Dept": "ViewRow [oracle.jbo.Key[30 ]]"
            },
            {
               "Empno": 7844,
               "Ename": "TURNER",
               "Job": "SALESMAN",
               "Mgr": 7698,
               "Hiredate": "1981-09-08 00:00:00.0",
               "Sal": 1500,
               "Comm": 0,
               "Deptno": 30,
               "Dept": "ViewRow [oracle.jbo.Key[30 ]]"
            },
            {
               "Empno": 7900,
               "Ename": "JAMES",
               "Job": "CLERK",
               "Mgr": 7698,
               "Hiredate": "1981-12-03 00:00:00.0",
               "Sal": 950,
               "Comm": null,
               "Deptno": 30,
               "Dept": "ViewRow [oracle.jbo.Key[30 ]]"
            }
         ]
      },
      {
         "Deptno": 40,
         "Dname": "OPERATIONS",
         "Loc": "BOSTON",
         "Emps": []
      }
   ]
}
```

