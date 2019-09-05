---
title: SqlClient pour Entity FrameworkTypes
ms.date: 03/30/2017
ms.assetid: f2a95ead-c845-4e97-9fb3-04b444f7ed81
ms.openlocfilehash: af3a4eea08dd3f4e1a134fcb66d92bc4a3b077c7
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248377"
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
|`decimal`|N/A|`Edm.Decimal`|Précision<br /><br /> Minimale 1<br /><br /> Valeurs 38<br /><br /> Valeurs 18<br /><br /> Suivantes False<br /><br /> Échelle<br /><br /> Minimale 0<br /><br /> Valeurs 38<br /><br /> Valeurs 0<br /><br /> Suivantes False|  
|`numeric`|N/A|`Edm.Decimal`|Précision<br /><br /> Minimale 1<br /><br /> Valeurs 38<br /><br /> Valeurs 18<br /><br /> Suivantes False<br /><br /> Échelle<br /><br /> Minimale 0<br /><br /> Valeurs 38<br /><br /> Valeurs 0<br /><br /> Suivantes False|  
|`smallmoney`|N/A|`Edm.Decimal`|Précision<br /><br /> Valeurs 10<br /><br /> Suivantes True<br /><br /> Échelle<br /><br /> Valeurs 4<br /><br /> Suivantes True|  
|`money`|N/A|`Edm.Decimal`|Précision<br /><br /> Valeurs 19<br /><br /> Suivantes True<br /><br /> Échelle<br /><br /> Valeurs 4<br /><br /> Suivantes True|  
|`binary`|N/A|`Edm.Binary`|MaxLength<br /><br /> Minimale 1<br /><br /> Valeurs 8000<br /><br /> Valeurs 8000<br /><br /> Suivantes False<br /><br /> Multiple<br /><br /> Valeurs True<br /><br /> Suivantes True|  
|`varbinary`|N/A|`Edm.Binary`|MaxLength<br /><br /> Minimale 1<br /><br /> Valeurs 8000<br /><br /> Valeurs 8000<br /><br /> Suivantes False<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`varbinary(max)`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.Binary`|MaxLength<br /><br /> Valeurs 214748364780<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`image`|N/A|`Edm.Binary`|MaxLength<br /><br /> Valeurs 2147483647<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`timestamp`|N/A|`Edm.Binary`|MaxLength<br /><br /> Valeurs 8<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs True<br /><br /> Suivantes True|  
|`rowversion`|N/A|`Edm.Binary`|MaxLength<br /><br /> Valeurs 8<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs True<br /><br /> Suivantes True|  
|`smalldatetime`|N/A|`Edm.DateTime`|Précision<br /><br /> Valeurs 0<br /><br /> Suivantes True|  
|`datetime`|N/A|`Edm.DateTime`|Précision<br /><br /> Valeurs 3<br /><br /> Suivantes True|  
|`date`<br /><br /> Remarque : Ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTime`|Précision<br /><br /> Valeurs 0<br /><br /> Suivantes False|  
|`time`<br /><br /> Remarque : Ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|N/A|`Edm.Time`|Précision<br /><br /> Valeurs 7<br /><br /> Suivantes False|  
|`datetime2`<br /><br /> Remarque : Ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTime`|Précision<br /><br /> Valeurs 7<br /><br /> Suivantes False|  
|`datetimeoffset`<br /><br /> Remarque : Ce type n’est pas pris en charge dans les SQL Server 2005 et SQL Server 2000.|N/A|`Edm.DateTimeOffset`|Précision<br /><br /> Valeurs 7<br /><br /> Suivantes False|  
|`nvarchar`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.String`|MaxLength<br /><br /> Minimale 1<br /><br /> Valeurs 4000<br /><br /> Valeurs 4000<br /><br /> Suivantes False<br /><br /> Unicode :<br /><br /> Valeurs True<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`varchar`<br /><br /> Remarque : Ce type n’est pas pris en charge dans SQL Server 2000.|N/A|`Edm.String`|MaxLength<br /><br /> Minimale 1<br /><br /> Valeurs 8000<br /><br /> Valeurs 8000<br /><br /> Suivantes False<br /><br /> Unicode :<br /><br /> Valeurs False<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`char`|N/A|`Edm.String`|MaxLength<br /><br /> Minimale 1<br /><br /> Valeurs 8000<br /><br /> Valeurs 8000<br /><br /> Suivantes False<br /><br /> Unicode :<br /><br /> Valeurs False<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs True<br /><br /> Suivantes True|  
|`nchar`|N/A|`Edm.String`|MaxLength<br /><br /> Minimale 1<br /><br /> Valeurs 4000<br /><br /> Valeurs 4000<br /><br /> Suivantes False<br /><br /> Unicode :<br /><br /> Valeurs True<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs True<br /><br /> Suivantes True|  
|`varchar`(`max`)|N/A|`Edm.String`|MaxLength<br /><br /> Valeurs 2147483647<br /><br /> Suivantes True<br /><br /> Unicode :<br /><br /> Valeurs False<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`nvarchar`(`max`)|N/A|`Edm.String`|MaxLength<br /><br /> Valeurs 1073741823<br /><br /> Suivantes True<br /><br /> Unicode :<br /><br /> Valeurs True<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`ntext`|Comparable identique : False<br /><br /> Comparable de l’ordre : False|`Edm.String`|MaxLength<br /><br /> Valeurs 1073741823<br /><br /> Suivantes True<br /><br /> Unicode :<br /><br /> Valeurs False<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`text`|Comparable identique : False<br /><br /> Comparable de l’ordre : False|`Edm.String`|MaxLength<br /><br /> Valeurs 2147483647<br /><br /> Suivantes True<br /><br /> Unicode :<br /><br /> Valeurs False<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
|`Unique`<br /><br /> `identifier`|Comparable identique : True<br /><br /> Comparable de l’ordre : True|`Edm.Guid`|N/A|  
|`xml`|Comparable identique : False<br /><br /> Comparable de l’ordre : False|`Edm.String`|MaxLength<br /><br /> Valeurs 1073741823<br /><br /> Suivantes True<br /><br /> Unicode :<br /><br /> Valeurs True<br /><br /> Suivantes True<br /><br /> Multiple<br /><br /> Valeurs False<br /><br /> Suivantes True|  
  
## <a name="see-also"></a>Voir aussi

- [Spécifications CSDL, SSDL et MSL](./language-reference/csdl-ssdl-and-msl-specifications.md)
