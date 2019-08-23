---
title: Attributs des paramètres d'application
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], attributes
- attributes [Windows Forms], application settings
- wrapper classes [Windows Forms], application settings
ms.assetid: 53caa66c-a9fb-43a5-953c-ad092590098d
ms.openlocfilehash: b38ed931cab3a333a56dd027d5843b1c8f00dcb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916681"
---
# <a name="application-settings-attributes"></a>Attributs des paramètres d'application
L’architecture des paramètres d’application fournit de nombreux attributs qui peuvent être appliqués à la classe wrapper de paramètres d’application ou à ses propriétés individuelles. Ces attributs sont examinés au moment de l’exécution par l’infrastructure des paramètres de l’application, souvent en particulier le fournisseur de paramètres, afin d’adapter son fonctionnement aux besoins spécifiés du wrapper personnalisé.  
  
 Le tableau suivant répertorie les attributs qui peuvent être appliqués à la classe wrapper de paramètres d’application, les propriétés individuelles de cette classe, ou les deux. Par définition, un seul attribut d’étendue (**UserScopedSettingAttribute** ou **ApplicationScopedSettingAttribute**) doit être appliqué à chaque propriété de paramètres.  
  
> [!NOTE]
> Un fournisseur de paramètres personnalisés, dérivé de <xref:System.Configuration.SettingsProvider> la classe, est uniquement requis pour reconnaître les trois attributs suivants: **ApplicationScopedSettingAttribute**, **UserScopedSettingAttribute**et **DefaultSettingValueAttribute**.  
  
|Attribut|Cible|Description|  
|---------------|------------|-----------------|  
|<xref:System.Configuration.SettingsProviderAttribute>|Les deux|Spécifie le nom abrégé du fournisseur de paramètres à utiliser pour la persistance.<br /><br /> Si cet attribut n’est pas fourni, le fournisseur par <xref:System.Configuration.LocalFileSettingsProvider>défaut,, est utilisé.|  
|<xref:System.Configuration.UserScopedSettingAttribute>|Les deux|Définit une propriété en tant que paramètre d’application de portée utilisateur.|  
|<xref:System.Configuration.ApplicationScopedSettingAttribute>|Les deux|Définit une propriété en tant que paramètre d’application de portée application.|  
|<xref:System.Configuration.DefaultSettingValueAttribute>|Propriété|Spécifie une chaîne qui peut être désérialisée par le fournisseur en valeur par défaut codée en dur pour cette propriété.<br /><br /> <xref:System.Configuration.LocalFileSettingsProvider> Ne requiert pas cet attribut, et remplace toute valeur fournie par cet attribut si une valeur est déjà persistante.|  
|<xref:System.Configuration.SettingsDescriptionAttribute>|Propriété|Fournit le test descriptif pour un paramètre individuel, principalement utilisé par les outils d’exécution et au moment du Design.|  
|<xref:System.Configuration.SettingsGroupNameAttribute>|Classe|Fournit un nom explicite pour un groupe de paramètres. Si cet attribut est manquant, <xref:System.Configuration.ApplicationSettingsBase> utilise le nom de la classe wrapper.|  
|<xref:System.Configuration.SettingsGroupDescriptionAttribute>|Classe|Fournit le test descriptif pour un groupe de paramètres, principalement utilisé par les outils d’exécution et au moment du Design.|  
|<xref:System.Configuration.SettingsManageabilityAttribute>|Les deux|Spécifie zéro, un ou plusieurs services de gestion qui doivent être fournis au groupe de paramètres ou à la propriété. Les services disponibles sont décrits par l' <xref:System.Configuration.SettingsManageability> énumération.|  
|<xref:System.Configuration.SpecialSettingAttribute>|Propriété|Indique qu’un paramètre appartient à une catégorie spéciale prédéfinie, telle qu’une chaîne de connexion, qui suggère un traitement spécial par le fournisseur de paramètres. Les catégories prédéfinies pour cet attribut sont définies par l' <xref:System.Configuration.SpecialSetting> énumération.|  
|<xref:System.Configuration.SettingsSerializeAsAttribute>|Les deux|Spécifie un mécanisme de sérialisation par défaut pour un groupe de paramètres ou une propriété. Les mécanismes de sérialisation disponibles sont définis par l' <xref:System.Configuration.SettingsSerializeAs> énumération.|  
|<xref:System.Configuration.NoSettingsVersionUpgradeAttribute>|Propriété|Spécifie qu’un fournisseur de paramètres doit désactiver toutes les fonctionnalités de mise à niveau d’application pour la propriété marquée.|  
  
 La *classe* indique que l’attribut peut être appliqué uniquement à une classe wrapper de paramètres d’application. La *propriété* indique que l’attribut peut être appliqué uniquement aux propriétés de paramètres. Les *deux* indiquent que l’attribut peut être appliqué à l’un ou l’autre niveau.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- [Architecture des paramètres d'application](application-settings-architecture.md)
- [Guide pratique : Créer des paramètres d’application](how-to-create-application-settings.md)
