---
title: Conventions de schéma de configuration de WIF
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: c02d467260a5197cdd01a3819f8a323655a8a08f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045098"
---
# <a name="wif-configuration-schema-conventions"></a>Conventions de schéma de configuration de WIF
Cette rubrique explique les conventions employées dans les rubriques traitant de la configuration de WIF (Windows Identity Foundation). Elle décrit également certaines fonctionnalités et attributs souvent utilisés dans les sections [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) et [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md).  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Modes  
 La plupart des éléments de configuration de WIF ont un attribut `mode`. Cet attribut détermine généralement la classe à utiliser pour effectuer certaines tâches du traitement, ainsi que les éléments de configuration qui peuvent être utilisés comme éléments enfants de l’élément actuel. Une erreur de configuration se produit si des éléments inclus dans le fichier de configuration sont ignorés en raison des paramètres de mode définis.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>Valeurs Timespan  
 Si <xref:System.TimeSpan> est utilisé comme type d’attribut, consultez la méthode <xref:System.TimeSpan.Parse%28System.String%29> pour connaître le format autorisé. Ce format respecte la spécification suivante.  
  
`[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]`  
  
 Par exemple, les valeurs « 30 », « 30.00:00 » et « 30.00:00:00 » représentent toutes une durée de 30 jours, et les valeurs « 00:05 », « 00:05:00 » et « 0.00:05:00.00 » représentent toutes une durée de 5 minutes.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Références à des certificats  
 Plusieurs éléments font référence à des certificats à l’aide de l’élément `<certificateReference>`. Pour faire référence à un certificat, vous pouvez utiliser les attributs suivants.  
  
|||  
|-|-|  
|`storeLocation`|Une valeur de l’énumération <xref:System.Security.Cryptography.X509Certificates.StoreLocation> : `CurrentUser` ou `CurrentMachine`.|  
|`storeName`|Une valeur de l’énumération <xref:System.Security.Cryptography.X509Certificates.StoreName>. Les valeurs `My` et `TrustedPeople` sont les plus utiles dans ce contexte.|  
|`x509FindType`|Une valeur de l’énumération <xref:System.Security.Cryptography.X509Certificates.X509FindType>. Les valeurs `FindBySubjectName` et `FindByThumbprint` sont les plus utiles dans ce contexte. Pour éliminer le risque d’erreur, il est recommandé d’utiliser le type `FindByThumbprint` dans les environnements de production.|  
|`findValue`|La valeur utilisée pour rechercher le certificat sur la base de l’attribut `x509FindType`. Pour éliminer le risque d’erreur, il est recommandé d’utiliser le type `FindByThumbprint` dans les environnements de production. Quand `FindByThumbPrint` est spécifié, cet attribut a une valeur représentant l’empreinte numérique du certificat au format de chaîne hexadécimale. Par exemple, « 97249e1a5fa6bee5e515b82111ef524a4c91583f ».|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Références à des types personnalisés  
 Plusieurs éléments peuvent faire référence à des types personnalisés à l’aide de l’attribut `type`. Cet attribut doit spécifier le nom du type personnalisé. Pour faire référence à un type à partir du Global Assembly Cache (GAC), utilisez un nom fort. Pour faire référence à un type à partir d’un assembly du répertoire Bin/, utilisez une référence qualifiée d’assembly simple. Les types définis dans le répertoire App_Code/ peuvent également être référencés simplement par le nom de type, sans référence d’assembly qualifiée.  
  
 Les types personnalisés doivent être dérivés du type spécifié et fournir un constructeur `public` par défaut (sans argument).  
  
## <a name="see-also"></a>Voir aussi

- [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)
- [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
