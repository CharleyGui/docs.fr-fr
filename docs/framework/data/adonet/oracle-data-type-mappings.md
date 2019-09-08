---
title: Mappages des types de données Oracle
ms.date: 03/30/2017
ms.assetid: ec34ae21-bbbb-4adb-b672-83865e2a8451
ms.openlocfilehash: be478741069e9edd406d73c0b75d5960b9909896
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783422"
---
# <a name="oracle-data-type-mappings"></a>Mappages des types de données Oracle
La table suivante répertorie les types de données Oracle et leurs mappages sur le <xref:System.Data.OracleClient.OracleDataReader>.  
  
|Type de données Oracle|Type de données .NET Framework retourné par OracleDataReader.GetValue|Type de données OracleClient retourné par OracleDataReader.GetOracleValue|Notes|  
|----------------------|--------------------------------------------------------------------|------------------------------------------------------------------------|-------------|  
|**BFILE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBFile>||  
|**BLOB**|**Byte[]**|<xref:System.Data.OracleClient.OracleLob>||  
|**CHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**DATE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**FLOAT**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le type de données **Number** et est conçu de telle <xref:System.Data.OracleClient.OracleDataReader> sorte que le retourne un **System. Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur à virgule flottante. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**ENTIÈRE**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le type de données **Number (38)** et est conçu de telle <xref:System.Data.OracleClient.OracleDataReader> sorte que le retourne un **System. Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur entière. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**INTERVALLE ANNÉE À MOIS**|**Int32**|<xref:System.Data.OracleClient.OracleMonthSpan>||  
|**INTERVALLE JOUR À SECONDE**|**TimeSpan**|<xref:System.Data.OracleClient.OracleTimeSpan>||  
|**LONG**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**LONG RAW**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**NCHAR**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**NCLOB**|**String**|<xref:System.Data.OracleClient.OracleLob>||  
|**CERTAIN**|**Decimal**|<xref:System.Data.OracleClient.OracleNumber>|L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**NVARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**PREMIÈRE**|**Byte[]**|<xref:System.Data.OracleClient.OracleBinary>||  
|**REF CURSOR**|||Le type de données Oracle **REF CURSOR** n’est pas pris <xref:System.Data.OracleClient.OracleDataReader> en charge par l’objet.|  
|**ID**|**String**|<xref:System.Data.OracleClient.OracleString>||  
|**CONFIRMÉ**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**HORODATEUR AVEC FUSEAU HORAIRE LOCAL**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**HORODATEUR AVEC FUSEAU HORAIRE**|**DateTime**|<xref:System.Data.OracleClient.OracleDateTime>||  
|**ENTIER NON SIGNÉ**|**Nombre**|<xref:System.Data.OracleClient.OracleNumber>|Ce type de données est un alias pour le type de données **Number (38)** et est conçu de telle <xref:System.Data.OracleClient.OracleDataReader> sorte que le retourne un **System. Decimal** ou <xref:System.Data.OracleClient.OracleNumber> au lieu d’une valeur entière non signée. L'utilisation du type de données .NET Framework peut entraîner un dépassement.|  
|**VARCHAR2**|**String**|<xref:System.Data.OracleClient.OracleString>||  
  
 Le tableau suivant répertorie les types de données Oracle et les types de données .NET Framework (**System. Data. DbType** et <xref:System.Data.OracleClient.OracleType>) à utiliser lors de leur liaison en tant que paramètres.  
  
|Type de données Oracle|Énumération DbType à lier comme paramètre|Énumération OracleType à lier comme paramètre|Notes|  
|----------------------|-----------------------------------------------|---------------------------------------------------|-------------|  
|**BFILE**||**BFile**|Oracle n’autorise la liaison d’un **BFILE** que comme paramètre **BFILE** . Le .NET Fournisseur de données pour Oracle n’en construit pas automatiquement un pour vous si vous tentez de lier une valeur non**BFILE** , telle que **Byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**BLOB**||**Blob**|Oracle n’autorise la liaison d’un **objet BLOB** qu’en tant que paramètre **BLOB** . Le .NET Fournisseur de données pour Oracle n’en construit pas automatiquement un pour vous si vous tentez de lier une valeur non-**BLOB** , telle que **Byte []** ou <xref:System.Data.OracleClient.OracleBinary>.|  
|**CHAR**|**AnsiStringFixedLength**|**Char**||  
|**CLOB**||**CLOB**|Oracle n’autorise la liaison d’un **CLOB** que comme paramètre **CLOB** . Le .NET Fournisseur de données pour Oracle n’en construit pas automatiquement un pour vous si vous tentez de lier une valeur non-**CLOB** , telle que **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**DATE**|**DateTime**|**DateTime**||  
|**FLOAT**|**Simple, double, décimal**|**Float, double, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>détermine les **System. Data. DbType** et <xref:System.Data.OracleClient.OracleType>.|  
|**ENTIÈRE**|**SByte, Int16, Int32, Int64, Decimal**|**SByte, Int16, Int32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>détermine les **System. Data. DbType** et <xref:System.Data.OracleClient.OracleType>.|  
|**INTERVALLE ANNÉE À MOIS**|**Int32**|**IntervalYearToMonth**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**INTERVALLE JOUR À SECONDE**|**Objet**|**IntervalDayToSecond**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**LONG**|**AnsiString**|**LongVarChar**||  
|**LONG RAW**|**Binary**|**LongRaw**||  
|**NCHAR**|**StringFixedLength**|**NChar**||  
|**NCLOB**||**NClob**|Oracle n’autorise la liaison d’un **NCLOB** que comme paramètre **NCLOB** . Le .NET Fournisseur de données pour Oracle n’en construit pas automatiquement un pour vous si vous tentez de lier une valeur non-**NCLOB** , telle que **System. String** ou <xref:System.Data.OracleClient.OracleString>.|  
|**CERTAIN**|**VarNumeric**|**Nombre**||  
|**NVARCHAR2**|**String**|**NVarChar**||  
|**PREMIÈRE**|**Binary**|**Première**||  
|**REF CURSOR**||**Mire**|Pour plus d’informations, consultez [Oracle REF Cursors](oracle-ref-cursors.md).|  
|**ID**|**AnsiString**|**ID**||  
|**CONFIRMÉ**|**DateTime**|**Timestamp**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**HORODATEUR AVEC FUSEAU HORAIRE LOCAL**|**DateTime**|**TimestampLocal**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**HORODATEUR AVEC FUSEAU HORAIRE**|**DateTime**|**TimestampWithTz**|<xref:System.Data.OracleClient.OracleType> est uniquement disponible lors de l'utilisation combinée du client Oracle 9i et du logiciel serveur.|  
|**ENTIER NON SIGNÉ**|**Byte, UInt16, UInt32, UInt64, Decimal**|**Byte, UInt16, UInt32, Number**|<xref:System.Data.OracleClient.OracleParameter.Size%2A>détermine les **System. Data. DbType** et <xref:System.Data.OracleClient.OracleType>.|  
|**VARCHAR2**|**AnsiString**|**VarChar**||  
  
 Les valeurs **InputOutput**, **Output**et **returnValue** **ParameterDirection** utilisées par la <xref:System.Data.OracleClient.OracleParameter.Value%2A> propriété de l' <xref:System.Data.OracleClient.OracleParameter> objet sont des types de données .NET Framework, sauf si la valeur d’entrée est un type de données Oracle (pour exemple, <xref:System.Data.OracleClient.OracleNumber> ou <xref:System.Data.OracleClient.OracleString>). Cela ne s’applique pas aux types de données **REF CURSOR**, **BFILE**ou **LOB** .  
  
## <a name="see-also"></a>Voir aussi

- [Oracle et ADO.NET](oracle-and-adonet.md)
- [Vue d’ensemble d’ADO.NET](ado-net-overview.md)
