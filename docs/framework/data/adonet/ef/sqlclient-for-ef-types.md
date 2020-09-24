---
title: SqlClient pour Entity FrameworkTypes
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: bca2cc0e0d9f43c51c66080f3bd38c245ce94381
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91156587"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient pour Entity FrameworkTypes

Le fichier de manifeste du fournisseur de données .NET Framework pour SQL Server (SqlClient) inclut la liste des types primitifs du fournisseur, les facettes de chaque type, les mappages entre les types primitifs des modèles conceptuels et de stockage, ainsi que les règles de promotion et de conversion entre les types primitifs des modèles conceptuels et de stockage.  
  
 Le tableau suivant décrit les types pour les bases de données SQL Server 2008, SQL Server 2005 et SQL Server 2000 et comment ces types sont mappés aux types de modèle conceptuel. Certains nouveaux types introduits dans les versions ultérieures de SQL Server ne sont pas pris en charge dans les versions antérieures de SQL Server. Ces types sont signalés dans le tableau ci-dessous.  
  
|Type de fournisseur<br /><br /> name|Type de fournisseur<br /><br /> attributs|`EDMSimpleType`<br /><br /> name|Choix multiples|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|n/a|`Edm.Boolean`|n/a|  
|`tinyint`|n/a|`Edm.Byte`|n/a|  
|`smallint`|n/a|`Edm.Int16`|n/a|  
|`int`|n/a|`Edm.Int32`|n/a|  
|`bigint`|n/a|`Edm.Int64`|n/a|  
|`float`|n/a|`Edm.Double`|n/a|  
|`real`|n/a|`Edm.Double`|n/a|  
|`decimal`|n/a|`Edm.Decimal`|Précision<br /><br /> -Minimum : 1<br /><br /> -Maximum : 38<br /><br /> -Par défaut : 18<br /><br /> -Constante : false<br /><br /> Échelle :<br /><br /> -Minimum : 0<br /><br /> -Maximum : 38<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : false|  
|`numeric`|n/a|`Edm.Decimal`|Précision<br /><br /> -Minimum : 1<br /><br /> -Maximum : 38<br /><br /> -Par défaut : 18<br /><br /> -Constante : false<br /><br /> Échelle :<br /><br /> -Minimum : 0<br /><br /> -Maximum : 38<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : false|  
|`smallmoney`|n/a|`Edm.Decimal`|Précision<br /><br /> -Par défaut : 10<br /><br /> -Constante : true<br /><br /> Échelle :<br /><br /> -Valeur par défaut : 4<br /><br /> -Constante : true|  
|`money`|n/a|`Edm.Decimal`|Précision<br /><br /> -Par défaut : 19<br /><br /> -Constante : true<br /><br /> Échelle :<br /><br /> -Valeur par défaut : 4<br /><br /> -Constante : true|  
|`binary`|n/a|`Edm.Binary`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constante : false<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`varbinary`|n/a|`Edm.Binary`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constante : false<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`varbinary(max)`<br /><br /> Remarque : ce type n’est pas pris en charge dans SQL Server 2000.|n/a|`Edm.Binary`|MaxLength<br /><br /> -Par défaut : 214748364780<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`image`|n/a|`Edm.Binary`|MaxLength<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`timestamp`|n/a|`Edm.Binary`|MaxLength<br /><br /> -Valeur par défaut : 8<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`rowversion`|n/a|`Edm.Binary`|MaxLength<br /><br /> -Valeur par défaut : 8<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`smalldatetime`|n/a|`Edm.DateTime`|Précision<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : true|  
|`datetime`|n/a|`Edm.DateTime`|Précision<br /><br /> -Par défaut : 3<br /><br /> -Constante : true|  
|`date`<br /><br /> Remarque : ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|n/a|`Edm.DateTime`|Précision<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : false|  
|`time`<br /><br /> Remarque : ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|n/a|`Edm.Time`|Précision<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : false|  
|`datetime2`<br /><br /> Remarque : ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|n/a|`Edm.DateTime`|Précision<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : false|  
|`datetimeoffset`<br /><br /> Remarque : ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|n/a|`Edm.DateTimeOffset`|Précision<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : false|  
|`nvarchar`<br /><br /> Remarque : ce type n’est pas pris en charge dans SQL Server 2000.|n/a|`Edm.String`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 4000<br /><br /> -Par défaut : 4000<br /><br /> -Constante : false<br /><br /> Unicode :<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`varchar`<br /><br /> Remarque : ce type n’est pas pris en charge dans SQL Server 2000.|n/a|`Edm.String`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constante : false<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`char`|n/a|`Edm.String`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constante : false<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`nchar`|n/a|`Edm.String`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 4000<br /><br /> -Par défaut : 4000<br /><br /> -Constante : false<br /><br /> Unicode :<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`varchar`(`max`)|n/a|`Edm.String`|MaxLength<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`nvarchar`(`max`)|n/a|`Edm.String`|MaxLength<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`ntext`|Égal comparable : faux<br /><br /> Ordre comparable : faux|`Edm.String`|MaxLength<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`text`|Égal comparable : faux<br /><br /> Ordre comparable : faux|`Edm.String`|MaxLength<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`Unique`<br /><br /> `identifier`|Égal comparable : true<br /><br /> Classement comparable : true|`Edm.Guid`|n/a|  
|`xml`|Égal comparable : faux<br /><br /> Ordre comparable : faux|`Edm.String`|MaxLength<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
  
## <a name="see-also"></a>Voir aussi

- [Spécifications CSDL, SSDL et MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
