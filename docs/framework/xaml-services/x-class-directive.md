---
title: x:Class, directive
ms.date: 03/30/2017
f1_keywords:
- x:Class
- xClass
- Class
helpviewer_keywords:
- Class attribute in XAML [XAML Services]
- XAML [XAML Services], x:Class attribute
- x:Class attribute [XAML Services]
ms.assetid: bc4a3d8e-76e2-423e-a5d1-159a023e82ec
ms.openlocfilehash: 7245b14ff2f765c1cfe96a2d49aec34eff7e8a17
ms.sourcegitcommit: 90f0bee0e8a416e45c78fa3ad4c91ef00e5228d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2019
ms.locfileid: "66722562"
---
# <a name="xclass-directive"></a>x:Class, directive
Configure la compilation du balisage XAML pour joindre des classes partielles entre le balisage et code-behind. La classe partielle du code est définie dans un fichier de code séparé dans un [!INCLUDE[TLA#tla_cls](../../../includes/tlasharptla-cls-md.md)] language, tandis que la classe partielle du balisage est créée par la génération de code pendant la compilation de XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML  
  
```  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`namespace`|Facultatif. Spécifie un [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] espace de noms qui contient la classe partielle identifiée par `classname`. Si `namespace` est spécifié, un point (.) sépare `namespace` et `classname`. Consultez la section Notes.|  
|`classname`|Obligatoire. Spécifie le [!INCLUDE[TLA2#tla_clr](../../../includes/tla2sharptla-clr-md.md)] nom de la classe partielle qui connecte le XAML chargé et votre code-behind pour ce XAML.|  
  
## <a name="dependencies"></a>Dépendances  
 `x:Class` peut être spécifiée qu’avec l’élément racine d’une production XAML. `x:Class` n’est pas valide sur n’importe quel objet qui a un parent dans la production XAML. Pour plus d’informations, consultez [ \[MS-XAML\] Section 4.3.1.6](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
## <a name="remarks"></a>Notes  
 Le `namespace` valeur peut contenir des points supplémentaires pour organiser des espaces de noms connexes en hiérarchies de noms, qui est une technique courante en programmation .NET Framework. Seul le dernier point dans une chaîne de `x:Class` valeurs est interprété pour séparer `namespace` et `classname.` la classe qui est utilisée en tant que `x:Class` ne peut pas être une classe imbriquée. Les classes imbriquées ne sont pas autorisés, car la détermination de la signification de points pour `x:Class` chaînes est ambigu si les classes imbriquées sont autorisées.  
  
 Dans existant de programmation de modèles qui utilisent `x:Class`, `x:Class` est facultatif en ce sens qu’il est entièrement valide d’avoir une page XAML ne dont aucun code-behind. Toutefois, cette fonctionnalité interagit avec les actions de génération comme implémenté par les infrastructures qui utilisent XAML. `x:Class` fonctionnalité est également influencée par les rôles que différentes classifications de contenu XAML dans un modèle d’application et dans le correspondantes des actions de génération. Si votre XAML déclare l’attribut de gestion des événements valeurs ou instancie des éléments personnalisés où les classes définies sont dans la classe code-behind, vous devez fournir le `x:Class` directive référence (ou [x : Subclass](x-subclass-directive.md)) à la classe appropriée pour le code-behind.  
  
 La valeur de la `x:Class` directive doit être une chaîne qui spécifie le nom qualifié complet d’une classe mais sans informations d’assembly (équivalent à la <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Pour les applications simples, vous pouvez omettre les informations d’espace de noms CLR si le code-behind est également structuré de cette manière (code commence au niveau de la classe).  
  
 Le fichier code-behind pour une définition de la page ou l’application doit être dans un fichier de code qui est inclus dans le cadre du projet qui produit une application compilée et implique la compilation du balisage. Vous devez suivre les règles de noms pour les classes CLR. Pour plus d’informations, consultez [instructions de conception Framework](../../standard/design-guidelines/index.md). Par défaut, la classe code-behind doit être `public`; Toutefois, vous pouvez le définir à un autre niveau d’accès à l’aide de la [x : ClassModifier, Directive](x-classmodifier-directive.md).  
  
 Cette interprétation de la `x:Class` attribut s’applique uniquement à une implémentation XAML basé sur CLR, en particulier pour les Services XAML .NET Framework. Autres implémentations XAML qui ne sont pas basées sur CLR et qui n’utilisent pas les Services XAML .NET Framework peuvent utiliser une formule de résolution différente pour la connexion au balisage XAML et code d’exécution de la sauvegarde. Pour plus d’informations sur les interprétations plus générales de `x:Class`, consultez [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).  
  
 Un certain niveau de l’architecture, la signification de `x:Class` n’est pas définie dans les Services XAML .NET Framework. Il s’agit, car les Services XAML .NET Framework ne spécifie pas le modèle de programmation par le XAML balisage et code de stockage sont connectés. Autres utilisations de la `x:Class` directive peut être implémentée par les infrastructures spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment connecter le balisage XAML et code-behind basé sur CLR. Chaque framework peut avoir ses propres actions de génération qui activent une partie du comportement ou des composants spécifiques qui doivent être inclus dans l’environnement de génération. Dans une infrastructure, les actions de génération peuvent également varier selon le langage CLR spécifique qui est utilisé pour le code-behind.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x : Class dans le modèle de programmation WPF  
 Dans les applications WPF et le modèle d’application WPF, `x:Class` peuvent être déclarés en tant qu’attribut pour tout élément qui est la racine d’un fichier XAML et est compilé (où le XAML est inclus dans un projet d’application WPF avec `Page` action de génération), ou pour le < C4 > <xref:System.Windows.Application>  racine dans la définition d’application d’une application WPF compilée. Déclaration `x:Class` sur un élément autre qu’une racine de la page ou de la racine de l’application, ou un fichier de WPF XAML qui n’est pas compilé, provoque une erreur de compilation sous le compilateur de .NET Framework 3.0 et .NET Framework 3.5 WPF XAML. Pour plus d’informations sur les autres aspects de `x:Class` gestion dans WPF, consultez [Code-Behind et XAML dans WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x : Class pour Windows Workflow Foundation  
 Pour Windows Workflow Foundation, `x:Class` nomme la classe d’une activité personnalisée entièrement composée en XAML, ou nomme la classe partielle de la page XAML pour un concepteur d’activités avec code-behind.  
  
## <a name="silverlight-usage-notes"></a>Remarques sur l’utilisation de Silverlight  
 `x:Class` pour Silverlight est documenté séparément. Pour plus d’informations, consultez [XAML Namespace (x :)) Fonctionnalités de langage (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=199081).  
  
## <a name="see-also"></a>Voir aussi

- [x:Subclass, directive](x-subclass-directive.md)
- [XAML et classes personnalisées pour WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier, directive](x-classmodifier-directive.md)
- [Types migrés de WPF vers System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
