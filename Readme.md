# 수정 사항
## 1. DB 정보 수정

> **수정** : application.properties 로그인 정보 수정 후, DBEAVER connection 도 수정 

<BR>

## 2. 페이지 로딩 오류 발생
> **원인** : WriteDTO 에서 오타

``` java
//수정 1
<select id="selectByUid" resultType="com.lec.spring.WriteDTO">

=>

<select id="selectByUid" resultType="com.lec.spring.domain.WriteDTO">

//수정 2
WHERE wr_uid = #{param0}

=>

WHERE wr_uid = #{param1}

//수정 3

DELETE FROM test_write WHERE uid = #{uid}

=>

DELETE FROM test_write WHERE wr_uid = #{uid}
```

## 3. 목록 수정시 오류 발생
> **원인** : updateOk.jsp 에서 오타

``` html
//수정 
location.href = "view.do?uid=${uid}";

=>

location.href = "view.do?uid=${param.uid}"; 
```