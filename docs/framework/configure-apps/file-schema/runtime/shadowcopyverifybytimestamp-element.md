---
title: Élément <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 160f14c856735e1ceac8635506aea52454faea43
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73115728"
---
# <a name="shadowcopyverifybytimestamp-element"></a>Élément \<shadowCopyVerifyByTimestamp>
Spécifie si les clichés instantanés utilisent le comportement de démarrage par défaut introduit dans le .NET Framework 4, ou repassent au comportement de démarrage des versions antérieures du .NET Framework.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie si les domaines d’application qui utilisent des clichés instantanés comparent les horodatages de l’assembly au démarrage, afin de déterminer si un assembly a été mis à jour avant de copier l’assembly.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|true|Au démarrage, copie uniquement les assemblys qui ont été mis à jour depuis leur dernière copie dans le répertoire des clichés instantanés. Il s’agit de la valeur par défaut pour le .NET Framework 4.|  
|false|Rétablit le comportement de démarrage des versions précédentes du .NET Framework, qui consistait à copier tous les fichiers au démarrage.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Remarques  
 À partir du .NET Framework 4, les assemblys sont des clichés instantanés uniquement si leurs horodatages indiquent qu’ils ont été modifiés depuis leur dernière copie dans le répertoire des clichés instantanés. Cela permet d’améliorer les temps de démarrage de nombreuses applications qui utilisent des clichés instantanés, comme décrit dans [clichés instantanés d’assemblys](../../../app-domains/shadow-copy-assemblies.md). Les applications qui ont un pourcentage élevé et la fréquence des mises à jour d’assembly peuvent ne pas tirer parti de ce changement de comportement. Dans ce cas, vous pouvez utiliser cet élément pour restaurer le comportement des versions précédentes du .NET Framework.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment désactiver le comportement de démarrage par défaut des clichés instantanés dans le .NET Framework 4 et rétablir le comportement de démarrage des versions précédentes du .NET Framework.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Clichés instantanés d'assemblys](../../../app-domains/shadow-copy-assemblies.md)
