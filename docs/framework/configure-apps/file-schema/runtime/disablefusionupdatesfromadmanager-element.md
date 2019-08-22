---
title: Élément <disableFusionUpdatesFromADManager>
ms.date: 03/30/2017
helpviewer_keywords:
- disableFusionUpdatesFromADManager element
- <disableFusionUpdatesFromADManager> element
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1923e70143ea2a158447eccdb35d347fe4f51ea
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663771"
---
# <a name="disablefusionupdatesfromadmanager-element"></a>\<disableFusionUpdatesFromADManager >, élément
Indique si le comportement par défaut, qui consiste à permettre à l’hôte du runtime de remplacer les paramètres de configuration d’un domaine d’application, est désactivé.  
  
 \<Élément de > de configuration  
\<Élément > du Runtime  
\<disableFusionUpdatesFromADManager>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|enabled|Attribut requis.<br /><br /> Spécifie si la capacité par défaut de remplacer les paramètres de fusion est désactivée.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Valeur|Description|  
|-----------|-----------------|  
|0|Ne désactivez pas la possibilité de remplacer les paramètres de fusion. Il s’agit du comportement par défaut, à partir du .NET Framework 4.|  
|1|Désactivez la possibilité de remplacer les paramètres de fusion. Cela revient au comportement des versions antérieures du .NET Framework.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|  
  
## <a name="remarks"></a>Notes  
 À partir du .NET Framework 4, le comportement par défaut consiste à autoriser <xref:System.AppDomainManager> l’objet à substituer des paramètres de configuration <xref:System.AppDomainSetup.ConfigurationFile%2A> à l’aide <xref:System.AppDomainSetup.SetConfigurationBytes%2A> de la propriété <xref:System.AppDomainSetup> ou de la méthode de l’objet qui est passé à votre implémentation. de la <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> méthode, dans votre sous-classe <xref:System.AppDomainManager>de. Pour le domaine d’application par défaut, les paramètres que vous modifiez remplacent ceux qui ont été spécifiés par le fichier de configuration de l’application. Pour les autres domaines d’application, ils remplacent les paramètres de configuration qui ont <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> été <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> passés à la méthode ou.  
  
 Vous pouvez transmettre de nouvelles informations de configuration ou passer la valeur`Nothing` null (dans Visual Basic) pour éliminer les informations de configuration qui ont été transmises.  
  
 Ne transmettez pas d’informations de configuration <xref:System.AppDomainSetup.ConfigurationFile%2A> à la fois <xref:System.AppDomainSetup.SetConfigurationBytes%2A> à la propriété et à la méthode. Si vous passez des informations de configuration aux deux, les informations que vous <xref:System.AppDomainSetup.ConfigurationFile%2A> passez à la propriété sont ignorées, car la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode remplace les informations de configuration du fichier de configuration de l’application. Si vous utilisez la <xref:System.AppDomainSetup.ConfigurationFile%2A> propriété, vous pouvez passer NULL (`Nothing` en Visual Basic) à la <xref:System.AppDomainSetup.SetConfigurationBytes%2A> méthode pour éliminer les octets de configuration qui ont été spécifiés dans l' <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=nameWithType> appel <xref:System.AppDomain.CreateDomain%2A?displayProperty=nameWithType> à la méthode ou.  
  
 En plus des informations de configuration, vous pouvez modifier les paramètres suivants sur <xref:System.AppDomainSetup> l’objet qui est passé à votre implémentation de <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> la <xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>méthode <xref:System.AppDomainSetup.ApplicationBase%2A>: <xref:System.AppDomainSetup.ApplicationName%2A>, <xref:System.AppDomainSetup.CachePath%2A>,, <xref:System.AppDomainSetup.DisallowBindingRedirects%2A> , <xref:System.AppDomainSetup.DisallowCodeDownload%2A>,, <xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>, ,,<xref:System.AppDomainSetup.LoaderOptimization%2A>,, et<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>. <xref:System.AppDomainSetup.PrivateBinPath%2A> <xref:System.AppDomainSetup.PrivateBinPathProbe%2A> <xref:System.AppDomainSetup.DynamicBase%2A> <xref:System.AppDomainSetup.ShadowCopyFiles%2A>  
  
 En guise d’alternative à `<disableFusionUpdatesFromADManager>` l’utilisation de l’élément, vous pouvez désactiver le comportement par défaut en créant un paramètre de registre ou en définissant une variable d’environnement. Dans le registre, créez une valeur DWORD nommée `COMPLUS_disableFusionUpdatesFromADManager` sous `HKCU\Software\Microsoft\.NETFramework` ou `HKLM\Software\Microsoft\.NETFramework`, puis définissez la valeur sur 1. Sur la ligne de commande, affectez la `COMPLUS_disableFusionUpdatesFromADManager` valeur 1 à la variable d’environnement.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment désactiver la possibilité de substituer des paramètres de fusion à l' `<disableFusionUpdatesFromADManager>` aide de l’élément.  
  
```xml  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Méthode de localisation des assemblys par le runtime](../../../deployment/how-the-runtime-locates-assemblies.md)
