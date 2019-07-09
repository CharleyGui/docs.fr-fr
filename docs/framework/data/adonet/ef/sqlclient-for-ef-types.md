---
title: SqlClient pour Entity FrameworkTypes
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: 7e3abe86128670656bfb2607b8531c9ceb0e4134
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662115"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient pour Entity FrameworkTypes
Le fichier de manifeste du fournisseur de données .NET Framework pour SQL Server (SqlClient) inclut la liste des types primitifs du fournisseur, les facettes de chaque type, les mappages entre les types primitifs des modèles conceptuels et de stockage, ainsi que les règles de promotion et de conversion entre les types primitifs des modèles conceptuels et de stockage.  
  
 Le tableau suivant décrit les types de bases de données SQL Server 2008, SQL Server 2005 et SQL Server 2000 et comment ces types sont mappés aux types de modèle conceptuel. Certains nouveaux types introduits dans les versions ultérieures de SQL Server ne sont pas pris en charge dans les versions antérieures de SQL Server. Ces types sont signalés dans le tableau ci-dessous.  
  
|Type de fournisseur<br /><br /> name|Type de fournisseur<br /><br /> attributs|`EDMSimpleType`<br /><br /> name|Facettes|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/A|`Edm.Boolean`|N/A|  
|`tinyint`|N/A|`Edm.Byte`|N/A|  
|`smallint`|N/A|`Edm.Int16`|N/A|  
|`int`|N/A|`Edm.Int32`|N/A|  
|`bigint`|N/A|`Edm.Int64`|N/A|  
|`float`|N/A|`Edm.Double`|N/A|  
|`real`|N/A|`Edm.Double`|N/A|  
|`decimal`|N/A|`Edm.Decimal`|Précision :<br /><br /> -Minimum : 1<br /><br /> -Maximum : 38<br /><br /> -Valeur par défaut : 18<br /><br /> -Constante : False<br /><br /> Mise à l’échelle :<br /><br /> -Minimum : 0<br /><br /> -Maximum : 38<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : False|  
|`numeric`|N/A|`Edm.Decimal`|Précision :<br /><br /> -Minimum : 1<br /><br /> -Maximum : 38<br /><br /> -Valeur par défaut : 18<br /><br /> -Constante : False<br /><br /> Mise à l’échelle :<br /><br /> -Minimum : 0<br /><br /> -Maximum : 38<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : False|  
|`smallmoney`|N/A|`Edm.Decimal`|Précision :<br /><br /> -Valeur par défaut : 10<br /><br /> -Constante : True<br /><br /> Mise à l’échelle :<br /><br /> -Valeur par défaut : 4<br /><br /> -Constante : True|  
|`money`|N/A|`Edm.Decimal`|Précision :<br /><br /> -Valeur par défaut : 19<br /><br /> -Constante : True<br /><br /> Mise à l’échelle :<br /><br /> -Valeur par défaut : 4<br /><br /> -Constante : True|  
|`binary`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Valeur par défaut : 8000<br /><br /> -Constante : False<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True|  
|`varbinary`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Valeur par défaut : 8000<br /><br /> -Constante : False<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`varbinary(max)`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Valeur par défaut : 214748364780<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`image`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Valeur par défaut : 2147483647<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`timestamp`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Valeur par défaut : 8<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True|  
|`rowversion`|N/A|`Edm.Binary`|MaxLength :<br /><br /> -Valeur par défaut : 8<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True|  
|`smalldatetime`|N/A|`Edm.DateTime`|Précision :<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : True|  
|`datetime`|N/A|`Edm.DateTime`|Précision :<br /><br /> -Valeur par défaut : 3<br /><br /> -Constante : True|  
|`date`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTime`|Précision :<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : False|  
|`time`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2005 et SQL Server 2000.|N/A|`Edm.Time`|Précision :<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : False|  
|`datetime2`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTime`|Précision :<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : False|  
|`datetimeoffset`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTimeOffset`|Précision :<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : False|  
|`nvarchar`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.String`|MaxLength :<br /><br /> -Minimum : 1<br /><br /> -Maximum : 4000<br /><br /> -Valeur par défaut : 4000<br /><br /> -Constante : False<br /><br /> Unicode :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`varchar`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.String`|MaxLength :<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Valeur par défaut : 8000<br /><br /> -Constante : False<br /><br /> Unicode :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`char`|N/A|`Edm.String`|MaxLength :<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Valeur par défaut : 8000<br /><br /> -Constante : False<br /><br /> Unicode :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True|  
|`nchar`|N/A|`Edm.String`|MaxLength :<br /><br /> -Minimum : 1<br /><br /> -Maximum : 4000<br /><br /> -Valeur par défaut : 4000<br /><br /> -Constante : False<br /><br /> Unicode :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True|  
|`varchar`(`max`)|N/A|`Edm.String`|MaxLength :<br /><br /> -Valeur par défaut : 2147483647<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`nvarchar`(`max`)|N/A|`Edm.String`|MaxLength :<br /><br /> -Valeur par défaut : 1073741823<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`ntext`|Comparable au niveau : False<br /><br /> Comparable en ordre : False|`Edm.String`|MaxLength :<br /><br /> -Valeur par défaut : 1073741823<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`text`|Comparable au niveau : False<br /><br /> Comparable en ordre : False|`Edm.String`|MaxLength :<br /><br /> -Valeur par défaut : 2147483647<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
|`Unique`<br /><br /> `identifier`|Comparable au niveau : True<br /><br /> Comparable en ordre : True|`Edm.Guid`|N/A|  
|`xml`|Comparable au niveau : False<br /><br /> Comparable en ordre : False|`Edm.String`|MaxLength :<br /><br /> -Valeur par défaut : 1073741823<br /><br /> -Constante : True<br /><br /> Unicode :<br /><br /> -Valeur par défaut : True<br /><br /> -Constante : True<br /><br /> FixedLength :<br /><br /> -Valeur par défaut : False<br /><br /> -Constante : True|  
  
## <a name="see-also"></a>Voir aussi

- [Spécifications CSDL, SSDL et MSL](../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
