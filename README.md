#数据库表结构



##用户权限

1. 样品接收员
2. 样品管理员
3. 办公室主任
4. 检测工程师
5. 检测室主任（待定）
6. 办公室职员（只能生成报告）
7. 审核人（1，2，3，4，5）

##RLCDCMCD：所有的列表数据

```
CREATE TABLE ANLM.RLCDCMCD
(
  CMITMCD  VARCHAR2(10 BYTE)编码ID                    NOT NULL,
  CLSCD    NUMBER(5),
  CMITMNM  VARCHAR2(20 BYTE)编码名称                  NOT NULL,
  CLSNM    VARCHAR2(50 BYTE)编码细项                     NOT NULL,
  DSC      VARCHAR2(50 BYTE),备注
  CLSENM   VARCHAR2(40 BYTE),编码英文名
  ORD      NUMBER(5)排序                            DEFAULT 0,
  MNGITM1  VARCHAR2(50 BYTE),编码细项1
  MNGITM2  VARCHAR2(50 BYTE),编码细项2
  MNGITM3  VARCHAR2(50 BYTE)编码细项3
)
```

CMITMCD属性

1. IMRAEWON:任务来源
2. REGIND:检验类别
3. 09:业务类别
4. STS:任务状态，表中没有数据
5. REQLVL：任务等级
6. SMPMNCOND 样品保存条件
7. SMPPROTYP 样品处理方式
8. RECTYPE 报告发送方式
9. SMPQTYUNT 计量单位

主检部门下拉框 在表RLCDLAB中
主检人下拉框  在表RLCDUSER中
样品模块下拉框 在表RLCDTPLN中

##RLCDCUST：委托单位表


```
CREATE TABLE ANLM.RLCDCUST
(
  REQRCD    VARCHAR2(20 BYTE)                   NOT NULL,
  REQER     VARCHAR2(50 BYTE),委托单位名称
  CUSTDIV   NUMBER(5),客户类别（委托单位类别）
  ZIP       VARCHAR2(10 BYTE),邮编
  ZIP2      VARCHAR2(10 BYTE),
  PADR      VARCHAR2(200 BYTE),地址
  PADR2     VARCHAR2(200 BYTE),
  RMGRNM    VARCHAR2(50 BYTE),委托人
  TOMAIL    VARCHAR2(100 BYTE),邮箱
  TELNO     VARCHAR2(30 BYTE),联系电话
  FAX       VARCHAR2(30 BYTE),传真号
  PCS_NO    VARCHAR2(30 BYTE),手机号
  DISCOUNT  NUMBER(5,2),折扣率
  ETC       VARCHAR2(2000 BYTE),
  BIZNO     VARCHAR2(20 BYTE),
  IDNO      VARCHAR2(20 BYTE),
  CEONM     VARCHAR2(50 BYTE),
  RESERVE1  VARCHAR2(100 BYTE),
  RESERVE2  VARCHAR2(100 BYTE),
  RESERVE3  VARCHAR2(100 BYTE),
  CGRADE    VARCHAR2(10 BYTE),
  C_DEPT    VARCHAR2(40 BYTE),
  C_MAN     VARCHAR2(40 BYTE),
  C_PHONE   VARCHAR2(40 BYTE),
  C_HP      VARCHAR2(40 BYTE)
);

```

##RLTSREQ：样品业务申请表（任务表）

```
CREATE TABLE ANLM.RLTSREQ
(
  REQNUM             VARCHAR2(13 BYTE),业务（任务）编号！
  TESTCLSNUM         NUMBER(4),样品模板！
  LABNUM             NUMBER(2),主检部门！
  IOFLG              NUMBER(2),业务类别！
  REQDT              DATE,受理日期！
  REQER              VARCHAR2(50 BYTE),委托单位！
  REQERID            VARCHAR2(20 BYTE),
  REQRSN             VARCHAR2(2000 BYTE),检验依据
  COARECTYP          NUMBER(5),报告发送方式
  UNCTYN             NUMBER(1),
  TTL                VARCHAR2(200 BYTE),任务名称！
  CMT                VARCHAR2(1000 BYTE),产品性状描述
  ZIP                VARCHAR2(10 BYTE),
  ZIP2               VARCHAR2(10 BYTE),
  PADR               VARCHAR2(100 BYTE),
  PADR2              VARCHAR2(100 BYTE),
  TEL                VARCHAR2(20 BYTE),
  STS                NUMBER(3),任务状态！
  TOTSUM             NUMBER(8),核价（根据登录个数计算总价）
  TESTCLSNM          VARCHAR2(50 BYTE),
  REQDEPTNM          VARCHAR2(50 BYTE),接收部门
  COANUM             NUMBER(5),
  INPUTER            VARCHAR2(20 BYTE),
  TERMDT             DATE,报告交付日期
  FINDT              DATE,
  DOCNUM             VARCHAR2(10 BYTE),
  SUBNUM             NUMBER(3),
  IDNO               VARCHAR2(18 BYTE),
  PCS                VARCHAR2(20 BYTE),手机号
  ADDREQ             VARCHAR2(1000 BYTE),检验项目及检验要求
  KOLASYN            NUMBER(1),
  SUBLOC             VARCHAR2(1000 BYTE),分包项目
  TIMESTAMP          DATE,
  RECDEPT            VARCHAR2(20 BYTE),
  RECDT              DATE,到样日期
  SMPCNT             NUMBER(4),登录个数
  TAXYN              NUMBER(1),
  TAXTYPE            VARCHAR2(10 BYTE),
  CFLG               NUMBER(1)                  DEFAULT 0,
  TOMAIL             VARCHAR2(40 BYTE),
  LABMGR             VARCHAR2(20 BYTE),主检人
  ROFFICE            VARCHAR2(20 BYTE),
  CEONM              VARCHAR2(10 BYTE),
  RMGRNM             VARCHAR2(50 BYTE),
  WEBFLG             NUMBER(3),检验类别！
  BIZNO              VARCHAR2(20 BYTE),
  CUSTDIV            VARCHAR2(10 BYTE),
  CONDT              DATE,
  CONEMPNO           VARCHAR2(20 BYTE),
  ORECDT             DATE,
  CFUSRID            VARCHAR2(20 BYTE),
  CFDT               DATE,
  CFRSN              VARCHAR2(200 BYTE),
  DISCOUNT           NUMBER(5,2),
  SMPPROTYP          NUMBER(5),样品处理方式
  CUSTADDINFO1       VARCHAR2(100 BYTE),受检单位
  CUSTADDINFO2       VARCHAR2(200 BYTE),生产单位
  REQLVL             NUMBER(5),任务等级
  F_IM_RAEWON        NUMBER(5),任务来源
  F_FAX_NUM          VARCHAR2(50 BYTE),
  F_SMP_MNG_COND     NUMBER(5),样品保存条件
  F_SMP_QTY          NUMBER(8,2),检验样品数量
  F_RESV_QTY         NUMBER(8,2),备份样品数量
  CUSTADDINFO1_ADDR  VARCHAR2(100 BYTE),受检单位地址
  CUSTADDINFO2_ADDR  VARCHAR2(100 BYTE),生产单位地址
  CUSTADDINFO1_ZIP   VARCHAR2(20 BYTE),受检单位邮编
  CUSTADDINFO2_ZIP   VARCHAR2(20 BYTE),生产单位邮编
  CUSTADDINFO1_TEL   VARCHAR2(30 BYTE),受检单位电话
  CUSTADDINFO2_TEL   VARCHAR2(30 BYTE),生产单位电话
  F_SMP_QTY_UNIT     NUMBER(5),样品剂量单位
  TESTADD            NUMBER(8,2)
)
```


##V_RLCDUSR-RLCDUSR

```
CREATE TABLE ANLM.RLCDUSR
(
  EMPNO    VARCHAR2(20 BYTE)                    NOT NULL,
  KORNAME  VARCHAR2(40 BYTE),接收人
  HEAD     VARCHAR2(22 BYTE),
  DEPT     VARCHAR2(50 BYTE),
  CODE     VARCHAR2(10 BYTE),
  SECT     VARCHAR2(30 BYTE),
  TEAM     VARCHAR2(16 BYTE),
  GRADE    VARCHAR2(20 BYTE),
  POSIT    VARCHAR2(20 BYTE),
  REGNO    VARCHAR2(20 BYTE),
  EXISTID  VARCHAR2(20 BYTE),
  FDATE    DATE,
  TDATE    DATE,
  TENPNO   VARCHAR2(20 BYTE),
  PWD      VARCHAR2(100 BYTE),
  EMAIL    VARCHAR2(50 BYTE),
  PCS      VARCHAR2(20 BYTE)手机号
)
```

KORNAME：接收人（InputerNM）


##RLTSSINFO：样品信息表

```
CREATE TABLE ANLM.RLTSSINFO
(
  REQNUM          VARCHAR2(13 BYTE)             NOT NULL,
  SMPINFONUM      VARCHAR2(10 BYTE),样品序号
  SMPDT           DATE,
  RCPDT           DATE,记录交付日期
  SMPNUM          NUMBER(4),样品类型（小）
  RCPNO           VARCHAR2(20 BYTE),报告编码
  SMPR            VARCHAR2(20 BYTE),
  STS             VARCHAR2(4 BYTE),
  JDG             NUMBER(1),
  TITM            NUMBER(3),
  MITM            NUMBER(3),
  TSMPVM          NUMBER(8,3),
  SMPCMT          VARCHAR2(100 BYTE),样品标记
  FLG             NUMBER(1),
  FEEUNT          NUMBER(8),
  SMPDESC         VARCHAR2(200 BYTE),抽样种类
  PRODLOC         VARCHAR2(100 BYTE),
  TYPENM          VARCHAR2(200 BYTE),商标（和等级一起）
  SPECNM          VARCHAR2(200 BYTE),型号规格
  PRODNO          VARCHAR2(200 BYTE),批号/编号
  PRODDT          DATE,生产日期
  RMRATIO         VARCHAR2(20 BYTE),保存位置
  COANO           VARCHAR2(100 BYTE),
  SPECCLSNUM      NUMBER(10),检验标准类别
  SPECREVNUM      NUMBER(10),检验标准
  DTLSPECNUM      NUMBER(10),
  U_SMPNUM        NUMBER(4),样品类型（中）
  JRESULT         NUMBER(5),
  SMPDIS          VARCHAR2(100 BYTE),
  F_LIMIT_DT      DATE,保质期
  F_PO_SUNG       VARCHAR2(40 BYTE),产地（省）
  F_PO_CITY       VARCHAR2(40 BYTE),产地（市）
  F_PICK_AREA1    VARCHAR2(40 BYTE),采样地点（省）
  F_PICK_AREA2    VARCHAR2(40 BYTE),采样地点（市）
  F_PICK_AREA3    VARCHAR2(40 BYTE),采样地点（县）
  F_SAMP_DOC_NO   VARCHAR2(40 BYTE),抽样单编号
  F_SAMP_RAEWON   NUMBER(8),样品来源
  F_SAMP_TOT_QTY  VARCHAR2(20 BYTE),采样基数
  F_PICK_METHOD   VARCHAR2(100 BYTE),抽样方法
  F_SAMPLER       VARCHAR2(30 BYTE),抽样人
  F_SAMPLE_MARK   VARCHAR2(100 BYTE),样品指标
  F_REMARK        VARCHAR2(300 BYTE),客户信息备注
  F_PICK_PLACE    VARCHAR2(100 BYTE),抽样地点
  F_GRADE         VARCHAR2(80 BYTE)等级（和商标一起）
)
```

##RLCDTITM：检测项目表（RLCDTUSR，RLCDLABUSR，RLCDLAB）

```
CREATE TABLE ANLM.RLCDTITM
(
  TESTITMNUM  NUMBER(8),检测项目编号
  TESTITMNM   VARCHAR2(100 BYTE),检测项目名称
  ITMKNM      VARCHAR2(100 BYTE),分析方法（中文）
  ITMENM      VARCHAR2(100 BYTE),分析方法（英文）
  FEE         NUMBER(8),费用
  ACTYN       NUMBER(1)                         NOT NULL,
  UNT         VARCHAR2(40 BYTE),
  FEEGRP      VARCHAR2(5 BYTE),
  TITMDEV1    NUMBER(4),
  TITMDEV2    NUMBER(4),
  ORD         NUMBER(4),
  LABNUM      NUMBER(2),
  KOLASYN     NUMBER(1),
  ADDCNT      NUMBER(3),
  ADDFEE      NUMBER(8),
  T_DAY       NUMBER(3),
  FEE1        NUMBER(2,1)                       DEFAULT 1,
  FEE2        NUMBER(2,1)                       DEFAULT 1.5,
  FEE3        NUMBER(2,1)                       DEFAULT 2,
  T_DAY2      NUMBER(3)                         DEFAULT 0,
  T_DAY3      NUMBER(3)                         DEFAULT 0,
  RMK         VARCHAR2(80 BYTE),
  M_A         VARCHAR2(10 BYTE),
  M_B         VARCHAR2(10 BYTE),
  M_C         VARCHAR2(10 BYTE),
  M_D         VARCHAR2(10 BYTE),
  M_E         VARCHAR2(10 BYTE),
  M_F         VARCHAR2(10 BYTE),
  M_G         VARCHAR2(10 BYTE),
  M_H         VARCHAR2(10 BYTE),
  M_I         VARCHAR2(10 BYTE),
  M_J         VARCHAR2(10 BYTE)
)
```


##RLCDTUSR：检测-用户对应表

```
CREATE TABLE ANLM.RLCDTUSR
(
  LABNUM      NUMBER(4),主检部门编号
  TUSRNUM     VARCHAR2(20 BYTE),检测用户编号
  TESTITMNUM  NUMBER(8),检测项目编号
  FLG         NUMBER(1),
  KOLASYN     NUMBER(1),
  KOLASSDT    DATE,
  KOLASEDT    DATE
)
```

##RLCDLABUSR：实验室检测用户表

```
CREATE TABLE ANLM.RLCDLABUSR
(
  LABNUM    NUMBER(2),主检部门编号
  EMPNO     VARCHAR2(20 BYTE),检测用户编号
  OUTSRTDT  DATE,
  OUTENDDT  DATE,
  TMPEMPNO  VARCHAR2(20 BYTE),
  KOLAS     VARCHAR2(1 BYTE)                    DEFAULT 'N'
)
```

##RLCDLAB:主检部门表

```
CREATE TABLE ANLM.RLCDLAB
(
  LABNUM  NUMBER(2),主检部门编号
  LAB     VARCHAR2(30 BYTE),主检部门名称
  DSC     VARCHAR2(50 BYTE),
  ACTYN   NUMBER(1)                             NOT NULL,
  DTPCD   VARCHAR2(10 BYTE),
  DTPNM   VARCHAR2(50 BYTE),
  FLAG    VARCHAR2(1 BYTE)                      DEFAULT 'N'
)
```

##RLTSRDOC：附件表

```
CREATE TABLE ANLM.RLTSRDOC
(
  REQDOCNO    NUMBER(10)                        NOT NULL,
  REQNUM      VARCHAR2(12 BYTE),样品编号（业务编号）
  DOCNM       VARCHAR2(50 BYTE),文件名称
  FNM         VARCHAR2(50 BYTE),文件名
  FEXT        VARCHAR2(10 BYTE),文件后缀
  FSIZ        NUMBER(10),文件大小
  CONTEXT     BLOB,文件内容
  SMPINFONUM  VARCHAR2(20 BYTE)
)

```
##第一级部门  在表RLCDDIVI中
```

CREATE TABLE ANLM.RLCDDIVI
(
  CODE     VARCHAR2(10 BYTE)                    NOT NULL,
  DIVINM   VARCHAR2(30 BYTE),部门名称
  DIVIENM  VARCHAR2(100 BYTE)部门名称（英文）
)
```

##第二级部门 RLCDDEPT
```

CREATE TABLE ANLM.RLCDDEPT
(
  CODE       VARCHAR2(10 BYTE)                  NOT NULL,
  DEPTNM     VARCHAR2(30 BYTE),
  DEPTENM    VARCHAR2(100 BYTE),
  ZIP1       VARCHAR2(3 BYTE),
  ZIP2       VARCHAR2(3 BYTE),
  ADDR1      VARCHAR2(50 BYTE),
  ADDR2      VARCHAR2(50 BYTE),
  TEL        VARCHAR2(50 BYTE),
  TAG        VARCHAR2(10 BYTE),
  DIVICD     VARCHAR2(10 BYTE),
  ORG_ORDER  NUMBER(3)
)
```
##RLCDLAB : 实验室分组

```
CREATE TABLE ANLM.RLCDLAB
(
  LABNUM  NUMBER(2)                             NOT NULL,
  LAB     VARCHAR2(30 BYTE),分析班组
  DSC     VARCHAR2(50 BYTE),
  ACTYN   NUMBER(1)激活                             NOT NULL,
  DTPCD   VARCHAR2(10 BYTE),部门名称
  DTPNM   VARCHAR2(50 BYTE),
  FLAG    VARCHAR2(1 BYTE)                      DEFAULT 'N'
)
```

##用户管理  RLCDUSER
```
CREATE TABLE ANLM.RLCDUSR
(
  EMPNO    VARCHAR2(20 BYTE) 客户标号                   NOT NULL,
  KORNAME  VARCHAR2(40 BYTE) 用户名称,
  HEAD     VARCHAR2(22 BYTE) ,
  DEPT     VARCHAR2(50 BYTE) 部门名称,
  CODE     VARCHAR2(10 BYTE) 部门名称编号,
  SECT     VARCHAR2(30 BYTE),
  TEAM     VARCHAR2(16 BYTE),
  GRADE    VARCHAR2(20 BYTE) 级别,
  POSIT    VARCHAR2(20 BYTE),
  REGNO    VARCHAR2(20 BYTE),
  EXISTID  VARCHAR2(20 BYTE) 激活,
  FDATE    DATE,
  TDATE    DATE,
  TENPNO   VARCHAR2(20 BYTE),
  PWD      VARCHAR2(100 BYTE),
  EMAIL    VARCHAR2(50 BYTE),
  PCS      VARCHAR2(20 BYTE)
)
```

##审核组管理  RLATBIZ

```
CREATE TABLE ANLM.RLATBIZ
(
  BIZCD   NUMBER(4)                             NOT NULL,
  LABNUM  NUMBER(4),
  RPTFLG  VARCHAR2(1 BYTE),
  BIZNM   VARCHAR2(20 BYTE),批准阶段名
  STEP    NUMBER(2),任务状态
  USRID   VARCHAR2(20 BYTE),批准人
  GRPNM   VARCHAR2(20 BYTE),批准组名
  FLG     NUMBER(1),
  DPTCD   VARCHAR2(10 BYTE),
  USRNM   VARCHAR2(10 BYTE),
  DSC     VARCHAR2(100 BYTE)业务说明
)
```

##二级部门表   RLCDDEPT

```
CREATE TABLE ANLM.RLCDDEPT
(
  CODE       VARCHAR2(10 BYTE)                  NOT NULL,
  DEPTNM     VARCHAR2(30 BYTE),部门名称
  DEPTENM    VARCHAR2(100 BYTE),部门英文名称
  ZIP1       VARCHAR2(3 BYTE),
  ZIP2       VARCHAR2(3 BYTE),
  ADDR1      VARCHAR2(50 BYTE),
  ADDR2      VARCHAR2(50 BYTE),
  TEL        VARCHAR2(50 BYTE),
  TAG        VARCHAR2(10 BYTE),
  DIVICD     VARCHAR2(10 BYTE),
  ORG_ORDER  NUMBER(3)
)
```

## 用户权限管理 SC_USER_ROLE

```
CREATE TABLE ANLM.SC_USER_ROLE
(
  SC_BU_CODE  VARCHAR2(20 BYTE)                 NOT NULL,
  EMPNO       VARCHAR2(20 BYTE)批准人                 NOT NULL,
  SYS_ID      VARCHAR2(10 BYTE)                 NOT NULL,
  ROLE_ID     VARCHAR2(20 BYTE)                 NOT NULL,
  CUSER       VARCHAR2(20 BYTE)                 DEFAULT 'NONE',
  CDATE       DATE                              DEFAULT SYSDATE,
  UUSER       VARCHAR2(20 BYTE)                 DEFAULT 'NONE',
  UDATE       DATE                              DEFAULT SYSDATE
)
```

}

##  RLCDHOLIDAY   节假日表
```
CREATE TABLE ANLM.RLCDHOLIDAY
(
  HOLIDT     DATE 日期                              NOT NULL,
  HOLIDTCMT  VARCHAR2(250 BYTE)内容                 NOT NULL,
  REPEATYN   CHAR(1 BYTE)重复                      DEFAULT 'N'                   NOT NULL
)
```
