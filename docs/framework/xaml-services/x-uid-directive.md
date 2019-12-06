---
title: x:Uid, directive
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], localizable content attribute
- XAML [XAML Services], x:Uid attribute
- x:Uid attribute [XAML Services]
- Uid attribute [XAML Services]
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
ms.openlocfilehash: 32cfd9ab0cf6037c731b619e81a7504ac92d5fb9
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837179"
---
# <a name="xuid-directive"></a>x:Uid, directive
Fournit un identificateur unique à des éléments de balisage. Dans de nombreux scénarios, cet identificateur unique est utilisé par les processus et les outils de localisation XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation des attributs XAML  
  
```xaml  
<object x:Uid="identifier"... />  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`identifier`|Chaîne créée manuellement ou générée automatiquement qui doit être unique dans un fichier lorsqu’elle est interprétée par un consommateur de `x:Uid`.|  
  
## <a name="remarks"></a>Notes  
 Dans [MS-XAML], `x:Uid` est défini en tant que directive. Pour plus d’informations, consultez [\[MS-XAML\] section 5.3.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 `x:Uid` est discrète de `x:Name` à la fois en raison du scénario de localisation XAML indiqué et de sorte que les identificateurs utilisés pour la localisation n’ont pas de dépendances vis-à-vis des implications du modèle de programmation de `x:Name`. En outre, `x:Name` est régi par la portée de code XAML. Toutefois, `x:Uid` n’est pas régie par un concept de langage XAML défini pour l’application de l’unicité. Les processeurs XAML à un sens large (les processeurs qui ne font pas partie du processus de localisation) ne sont pas censés garantir l’unicité des valeurs de `x:Uid`. Cette responsabilité est conceptuellement sur l’expéditeur des valeurs. L’unicité des valeurs de `x:Uid` dans une source XAML unique est raisonnable pour les consommateurs des valeurs, telles que les processus de globalisation dédiés ou les outils. Le modèle d’unicité standard est que les valeurs `x:Uid` sont uniques dans un fichier encodé en XML qui représente du code XAML.  
  
 Les outils qui ont une connaissance significative d’un schéma XAML particulier peuvent choisir d’appliquer des `x:Uid` uniquement pour les véritables chaînes localisables, plutôt que pour tous les cas où une valeur de chaîne de texte est rencontrée dans le balisage.  
  
 Les infrastructures peuvent spécifier une propriété particulière dans leur modèle objet en tant qu’alias pour `x:Uid` en appliquant l’attribut <xref:System.Windows.Markup.UidPropertyAttribute> au type de définition. Si une infrastructure spécifie une propriété particulière, il n’est pas possible de spécifier à la fois `x:Uid` et le membre avec alias sur le même objet. Si `x:Uid` et le membre avec alias sont spécifiés, l’API des services XAML .NET Framework lève généralement <xref:System.Xaml.XamlDuplicateMemberException> pour ce cas.  
  
## <a name="wpf-usage-notes"></a>Remarques sur l’utilisation de WPF  
 Pour plus d’informations sur le rôle d' `x:Uid` dans le processus de localisation WPF et dans le formulaire BAML de XAML, consultez [globalisation for WPF](../wpf/advanced/globalization-for-wpf.md) or <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>
- <xref:Microsoft.Build.Tasks.Windows.UidManager>
- [Globalisation pour WPF](../wpf/advanced/globalization-for-wpf.md)
