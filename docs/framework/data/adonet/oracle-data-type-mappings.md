---
title: Mappages des types de données Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: 71a85f82ea3535cf7aec8dd92fbda6726a36fb81
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166571"
---
# <a name="oracle-data-type-mappings"></a>Mappages des types de données Oracle

La table suivante répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Type de données Oracle|Type de données .NET Framework retourné par OracleDataReader.GetValue|Type de données OracleClient retourné par OracleDataReader.GetOracleValue|Notes|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte []**|<xref:System.Data.OracleClient.OracleBFile>||  
|**OBJET BLOB**|**Byte []**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**Chaîne**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Décimal**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le type de données **Number** et est conçu de telle sorte que le <xref:System.Data.OracleClient.OracleDataReader> retourne un **System. Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur à virgule flottante. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**INTEGER**|**Décimal**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le type de données **Number (38)** et est conçu de telle sorte que le <xref:System.Data.OracleClient.OracleDataReader> retourne un **System. Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur entière. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**INTERVAL YEAR TO MONTH**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVAL DAY TO SECOND**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**Chaîne**|<xref:System.Data.OracleClient.OracleLob>||  
|**CERTAIN**|**Décimal**|<xref:System.Data.OracleClient.OracleNumber>|L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**NVARCHAR2**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**RAW**|**Byte []**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Le type de données Oracle **REF CURSOR** n’est pas pris en charge par l' <xref:System.Data.OracleClient.OracleDataReader> objet.|  
|**ROWID**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
|**TIMESTAMP**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**HORODATEUR AVEC FUSEAU HORAIRE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ENTIER NON SIGNÉ**|**Nombre**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le type de données **Number (38)** et est conçu de telle sorte que le <xref:System.Data.OracleClient.OracleDataReader> retourne un **System. Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur entière non signée. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**VARCHAR2**|**Chaîne**|<xref:System.Data.OracleClient.OracleString>||  
  
 Le tableau suivant répertorie les types de données Oracle et les types de données .NET Framework (**System. Data. DbType** et <xref:System.Data.OracleClient.OracleType> ) à utiliser lors de leur liaison en tant que paramètres.  
  
|Type de données Oracle|Énumération DbType à lier comme paramètre|Énumération OracleType à lier comme paramètre|Notes|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle n’autorise la liaison d’un **BFILE** que comme paramètre **BFILE** . Le .NET Fournisseur de données pour Oracle n’en construit pas automatiquement un pour vous si vous tentez de lier une valeur non**BFILE** , telle que **Byte []** ou <xref:System.Data.OracleClient.OracleBinary> .|  
|**OBJET BLOB**||**Objet blob**|Oracle n’autorise la liaison d’un **objet BLOB** qu’en tant que paramètre **BLOB** . Le .NET Fournisseur de données pour Oracle n’en construit pas automatiquement un pour vous si vous tentez de lier une valeur non-**BLOB** , telle que **Byte []** ou <xref:System.Data.OracleClient.OracleBinary> .|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**CLOB**|Oracle n’autorise la liaison d’un **CLOB** que comme paramètre **CLOB** . Le .NET Fournisseur de données pour Oracle n’en construit pas automatiquement un pour vous si vous tentez de lier une valeur non-**CLOB** , telle que **System. String** ou <xref:System.Data.OracleClient.OracleString> .|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Simple, double, décimal**|**Float, Double, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> détermine les **System. Data. DbType** et <xref:System.Data.OracleClient.OracleType> .|  
|**INTEGER**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> détermine les **System. Data. DbType** et <xref:System.Data.OracleClient.OracleType> .|  
|**INTERVAL YEAR TO MONTH**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**INTERVAL DAY TO SECOND**|**Object**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binaire**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle n’autorise la liaison d’un **NCLOB** que comme paramètre **NCLOB** . Le .NET Fournisseur de données pour Oracle n’en construit pas automatiquement un pour vous si vous tentez de lier une valeur non-**NCLOB** , telle que **System. String** ou <xref:System.Data.OracleClient.OracleString> .|  
|**CERTAIN**|**VarNumeric**|**Nombre**||  
|**NVARCHAR2**|**Chaîne**|**NVarChar**||  
|**RAW**|**Binaire**|**Brut**||  
|**REF CURSOR**||**Curseur**|Pour plus d’informations, consultez [Oracle REF Cursors](oracle-ref-cursors.md).|  
|**ROWID**|**AnsiString**|**ID**||  
|**TIMESTAMP**|**DateTime**|**Timestamp**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**TIMESTAMP WITH LOCAL TIME ZONE**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**HORODATEUR AVEC FUSEAU HORAIRE**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**ENTIER NON SIGNÉ**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, Uint32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A> détermine les **System. Data. DbType** et <xref:System.Data.OracleClient.OracleType> .|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 Les valeurs **InputOutput**, **Output**et **returnValue** **ParameterDirection** utilisées par la <xref:System.Data.OracleClient.OracleParameter.Value%2A> propriété de l' <xref:System.Data.OracleClient.OracleParameter> objet sont des types de données .NET Framework, sauf si la valeur d’entrée est un type de données Oracle (par exemple, <xref:System.Data.OracleClient.OracleNumber> ou <xref:System.Data.OracleClient.OracleString> ). Cela ne s’applique pas aux types de données **REF CURSOR**, **BFILE**ou **LOB** .  
  
## <a name="see-also"></a>Voir aussi

- [Oracle et ADO.NET](oracle-and-adonet.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
