---
title: Mappages de types de données OLE DB
ms.date: 03/30/2017
ms.assetid: 04bcb259-59d3-4fd7-894d-4f0dd0c68069
ms.openlocfilehash: 7f3b498e39feac4a6fe98e739793d20e0268b8f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150698"
---
# <a name="ole-db-data-type-mappings"></a>Mappages de types de données OLE DB

Le tableau suivant indique le type de .NET Framework déduit pour les types de données du .NET Framework Fournisseur de données pour ADO et OLE DB ( <xref:System.Data.OleDb> ). Les méthodes d’accesseur typées pour le <xref:System.Data.OleDb.OleDbDataReader> sont également répertoriées.  
  
|Type ADO|Type OLE DB|Type .NET Framework|Accesseur typé .NET Framework|  
|--------------|-----------------|----------------------------------------------------------------------|--------------------------------------------------------------------------------|  
|adBigInt|DBTYPE_I8|Int64|GetInt64()|  
|adBinary|DBTYPE_BYTES|Byte[]|GetBytes()|  
|adBoolean|DBTYPE_BOOL|Boolean|GetBoolean()|  
|adBSTR|DBTYPE_BSTR|String|GetString()|  
|adChapter|DBTYPE_HCHAPTER|Pris en charge dans le `DataReader`. Consultez [récupération de données à l’aide d’un DataReader](retrieving-data-using-a-datareader.md).|GetValue()|  
|adChar|DBTYPE_STR|String|GetString()|  
|adCurrency|DBTYPE_CY|Decimal|GetDecimal()|  
|adDate|DBTYPE_DATE|DateTime|GetDateTime()|  
|adDBDate|DBTYPE_DBDATE|DateTime|GetDateTime()|  
|adDBTime|DBTYPE_DBTIME|DateTime|GetDateTime()|  
|adDBTimeStamp|DBTYPE_DBTIMESTAMP|DateTime|GetDateTime()|  
|adDecimal|DBTYPE_DECIMAL|Decimal|GetDecimal()|  
|adDouble|DBTYPE_R8|Double|GetDouble()|  
|adError|DBTYPE_ERROR|ExternalException|GetValue()|  
|adFileTime|DBTYPE_FILETIME|DateTime|GetDateTime()|  
|adGUID|DBTYPE_GUID|Guid|GetGuid()|  
|adIDispatch|DBTYPE_IDISPATCH *|Object|GetValue()|  
|adInteger|DBTYPE_I4|Int32|GetInt32()|  
|adIUnknown|DBTYPE_IUNKNOWN *|Object|GetValue()|  
|adNumeric|DBTYPE_NUMERIC|Decimal|GetDecimal()|  
|adPropVariant|DBTYPE_PROPVARIANT|Object|GetValue()|  
|adSingle|DBTYPE_R4|Unique|GetFloat()|  
|adSmallInt|DBTYPE_I2|Int16|GetInt16()|  
|adTinyInt|DBTYPE_I1|Byte|GetByte()|  
|adUnsignedBigInt|DBTYPE_UI8|UInt64|GetValue()|  
|adUnsignedInt|DBTYPE_UI4|UInt32|GetValue()|  
|adUnsignedSmallInt|DBTYPE_UI2|UInt16|GetValue()|  
|adUnsignedTinyInt|DBTYPE_UI1|Byte|GetByte()|  
|adVariant|DBTYPE_VARIANT|Object|GetValue()|  
|adWChar|DBTYPE_WSTR|String|GetString()|  
|adUserDefined|DBTYPE_UDT|non pris en charge||  
|adVarNumeric|DBTYPE_VARNUMERIC|non pris en charge||  
  
 \* Pour les types de OLE DB `DBTYPE_IUNKNOWN` et `DBTYPE_IDISPATCH` , la référence d’objet est une représentation marshalée du pointeur.  
  
## <a name="see-also"></a>Voir aussi

- [Extraction et modification de données dans ADO.NET](retrieving-and-modifying-data.md)
- [Vue d'ensemble d’ADO.NET](ado-net-overview.md)
