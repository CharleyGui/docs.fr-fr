---
title: SqlClient pour Entity FrameworkTypes
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: d132583bba2520d37693be6c4b085cfa514003e0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737849"
---
# <a name="sqlclient-for-entity-frameworktypes"></a>SqlClient pour Entity FrameworkTypes
Le fichier de manifeste du fournisseur de données .NET Framework pour SQL Server (SqlClient) inclut la liste des types primitifs du fournisseur, les facettes de chaque type, les mappages entre les types primitifs des modèles conceptuels et de stockage, ainsi que les règles de promotion et de conversion entre les types primitifs des modèles conceptuels et de stockage.  
  
 Le tableau suivant décrit les types pour les bases de données SQL Server 2008, SQL Server 2005 et SQL Server 2000 et comment ces types sont mappés aux types de modèle conceptuel. Certains nouveaux types introduits dans les versions ultérieures de SQL Server ne sont pas pris en charge dans les versions antérieures de SQL Server. Ces types sont signalés dans le tableau ci-dessous.  
  
|Type de fournisseur<br /><br /> name|Type de fournisseur<br /><br /> attributs|`EDMSimpleType`<br /><br /> name|Facettes|  
|----------------------------|----------------------------------|------------------------------|------------|  
|`bit`|N/A|`Edm.Boolean`|N/A|  
|`tinyint`|N/A|`Edm.Byte`|N/A|  
|`smallint`|N/A|`Edm.Int16`|N/A|  
|`int`|N/A|`Edm.Int32`|N/A|  
|`bigint`|N/A|`Edm.Int64`|N/A|  
|`float`|N/A|`Edm.Double`|N/A|  
|`real`|N/A|`Edm.Double`|N/A|  
|`decimal`|N/A|`Edm.Decimal`|Précision<br /><br /> -Minimum : 1<br /><br /> -Maximum : 38<br /><br /> -Par défaut : 18<br /><br /> -Constante : false<br /><br /> Échelle<br /><br /> -Minimum : 0<br /><br /> -Maximum : 38<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : false|  
|`numeric`|N/A|`Edm.Decimal`|Précision<br /><br /> -Minimum : 1<br /><br /> -Maximum : 38<br /><br /> -Par défaut : 18<br /><br /> -Constante : false<br /><br /> Échelle<br /><br /> -Minimum : 0<br /><br /> -Maximum : 38<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : false|  
|`smallmoney`|N/A|`Edm.Decimal`|Précision<br /><br /> -Par défaut : 10<br /><br /> -Constante : true<br /><br /> Échelle<br /><br /> -Valeur par défaut : 4<br /><br /> -Constante : true|  
|`money`|N/A|`Edm.Decimal`|Précision<br /><br /> -Par défaut : 19<br /><br /> -Constante : true<br /><br /> Échelle<br /><br /> -Valeur par défaut : 4<br /><br /> -Constante : true|  
|`binary`|N/A|`Edm.Binary`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constante : false<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`varbinary`|N/A|`Edm.Binary`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constante : false<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`varbinary(max)`<br /><br /> Remarque : ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.Binary`|MaxLength<br /><br /> -Par défaut : 214748364780<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`image`|N/A|`Edm.Binary`|MaxLength<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`timestamp`|N/A|`Edm.Binary`|MaxLength<br /><br /> -Valeur par défaut : 8<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`rowversion`|N/A|`Edm.Binary`|MaxLength<br /><br /> -Valeur par défaut : 8<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`smalldatetime`|N/A|`Edm.DateTime`|Précision<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : true|  
|`datetime`|N/A|`Edm.DateTime`|Précision<br /><br /> -Par défaut : 3<br /><br /> -Constante : true|  
|`date`<br /><br /> Remarque : ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTime`|Précision<br /><br /> -Valeur par défaut : 0<br /><br /> -Constante : false|  
|`time`<br /><br /> Remarque : ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|N/A|`Edm.Time`|Précision<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : false|  
|`datetime2`<br /><br /> Remarque : ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTime`|Précision<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : false|  
|`datetimeoffset`<br /><br /> Remarque : ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTimeOffset`|Précision<br /><br /> -Valeur par défaut : 7<br /><br /> -Constante : false|  
|`nvarchar`<br /><br /> Remarque : ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.String`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 4000<br /><br /> -Par défaut : 4000<br /><br /> -Constante : false<br /><br /> Unicode :<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`varchar`<br /><br /> Remarque : ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.String`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constante : false<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`char`|N/A|`Edm.String`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 8000<br /><br /> -Par défaut : 8000<br /><br /> -Constante : false<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`nchar`|N/A|`Edm.String`|MaxLength<br /><br /> -Minimum : 1<br /><br /> -Maximum : 4000<br /><br /> -Par défaut : 4000<br /><br /> -Constante : false<br /><br /> Unicode :<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true|  
|`varchar`(`max`)|N/A|`Edm.String`|MaxLength<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`nvarchar`(`max`)|N/A|`Edm.String`|MaxLength<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`ntext`|Égal comparable : faux<br /><br /> Ordre comparable : faux|`Edm.String`|MaxLength<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`text`|Égal comparable : faux<br /><br /> Ordre comparable : faux|`Edm.String`|MaxLength<br /><br /> -Par défaut : 2147483647<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
|`Unique`<br /><br /> `identifier`|Égal comparable : true<br /><br /> Classement comparable : true|`Edm.Guid`|N/A|  
|`xml`|Égal comparable : faux<br /><br /> Ordre comparable : faux|`Edm.String`|MaxLength<br /><br /> -Par défaut : 1073741823<br /><br /> -Constante : true<br /><br /> Unicode :<br /><br /> -Valeur par défaut : true<br /><br /> -Constante : true<br /><br /> Multiple<br /><br /> -Valeur par défaut : false<br /><br /> -Constante : true|  
  
## <a name="see-also"></a>Voir aussi

- [Spécifications CSDL, SSDL et MSL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
