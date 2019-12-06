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
ms.openlocfilehash: d6baa6d8eb3a6d3520fb1549e2182f27ca52c36a
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837244"
---
# <a name="xclass-directive"></a>x:Class, directive
Configure la compilation du balisage XAML pour joindre des classes partielles entre le balisage et le code-behind. La classe partielle du code est définie dans un fichier de code séparé dans un langage Common Language Specification (CLS), tandis que la classe partielle du balisage est généralement créée par la génération de code pendant la compilation XAML.  
  
## <a name="xaml-attribute-usage"></a>Utilisation des attributs XAML  
  
```xaml  
<object x:Class="namespace.classname"...>  
  ...  
</object>  
```  
  
## <a name="xaml-values"></a>Valeurs XAML  
  
|||  
|-|-|  
|`namespace`|Option facultative. Spécifie un espace de noms CLR qui contient la classe partielle identifiée par `classname`. Si `namespace` est spécifié, un point (.) sépare `namespace` et `classname`. Consultez la section Notes.|  
|`classname`|Requis. Spécifie le nom CLR de la classe partielle qui connecte le XAML chargé et votre code-behind pour ce XAML.|  
  
## <a name="dependencies"></a>Dépendances  
 `x:Class` peut uniquement être spécifié sur l’élément racine d’une production XAML. `x:Class` n’est pas valide sur un objet qui a un parent dans la production XAML. Pour plus d’informations, consultez [\[MS-XAML\] section 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
## <a name="remarks"></a>Notes  
 La valeur `namespace` peut contenir des points supplémentaires pour organiser les espaces de noms associés en hiérarchies de noms, ce qui est une technique courante dans la programmation .NET Framework. Seul le dernier point d’une chaîne de `x:Class` valeurs est interprété pour séparer `namespace` et `classname.` la classe utilisée comme `x:Class` ne peut pas être une classe imbriquée. Les classes imbriquées ne sont pas autorisées, car la détermination de la signification des points pour `x:Class` chaînes est ambiguë si les classes imbriquées sont autorisées.  
  
 Dans les modèles de programmation existants qui utilisent `x:Class`, `x:Class` est facultatif dans le sens où il est entièrement valide de disposer d’une page XAML qui n’a pas de code-behind. Toutefois, cette fonctionnalité interagit avec les actions de génération telles qu’elles sont implémentées par les frameworks qui utilisent XAML. `x:Class` fonctionnalité est également influencée par les rôles que différentes classifications de contenu spécifiés en XAML possèdent dans un modèle d’application et dans les actions de génération correspondantes. Si votre code XAML déclare des valeurs d’attribut de gestion d’événements ou instancie des éléments personnalisés où les classes de définition se trouvent dans la classe code-behind, vous devez fournir la référence de directive `x:Class` (ou [x :Subclass](x-subclass-directive.md)) à la classe appropriée pour le code-behind.  
  
 La valeur de la directive `x:Class` doit être une chaîne qui spécifie le nom qualifié complet d’une classe mais sans aucune information d’assembly (équivalent à la <xref:System.Type.FullName%2A?displayProperty=nameWithType>). Pour les applications simples, vous pouvez omettre les informations d’espace de noms CLR si le code-behind est également structuré de cette manière (la définition de code commence au niveau de la classe).  
  
 Le fichier code-behind pour une définition de page ou d’application doit figurer dans un fichier de code inclus dans le cadre du projet qui produit une application compilée et implique la compilation du balisage. Vous devez suivre les règles de nom pour les classes CLR. Pour plus d’informations, consultez [instructions de conception d’infrastructure](../../standard/design-guidelines/index.md). Par défaut, la classe code-behind doit être `public`; Toutefois, vous pouvez le définir à un niveau d’accès différent à l’aide de la [directive x :ClassModifier](x-classmodifier-directive.md).  
  
 Cette interprétation de l’attribut `x:Class` s’applique uniquement à une implémentation XAML basée sur CLR, en particulier pour .NET Framework les services XAML. D’autres implémentations XAML qui ne sont pas basées sur CLR et qui n’utilisent pas de .NET Framework les services XAML peuvent utiliser une formule de résolution différente pour connecter le balisage XAML et le code d’exécution de sauvegarde. Pour plus d’informations sur les interprétations plus générales de `x:Class`, consultez [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).  
  
 À un certain niveau d’architecture, la signification de `x:Class` n’est pas définie dans .NET Framework les services XAML. Cela est dû au fait que .NET Framework les services XAML ne spécifient pas le modèle de programmation par lequel le balisage XAML et le code de stockage sont connectés. Des utilisations supplémentaires de la directive `x:Class` peuvent être implémentées par des frameworks spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment connecter le balisage XAML et le code-behind basé sur CLR. Chaque infrastructure peut avoir ses propres actions de génération qui activent certains des comportements ou des composants spécifiques qui doivent être inclus dans l’environnement de génération. Dans une infrastructure, les actions de génération peuvent également varier en fonction du langage CLR spécifique utilisé pour le code-behind.  
  
## <a name="xclass-in-the-wpf-programming-model"></a>x :Class dans le modèle de programmation WPF  
 Dans les applications WPF et le modèle d’application WPF, `x:Class` peut être déclaré en tant qu’attribut pour tout élément qui est la racine d’un fichier XAML et qui est en cours de compilation (où le code XAML est inclus dans un projet d’application WPF avec `Page` action de génération), ou pour la racine de <xref:System.Windows.Application> dans la définition d’application d’une application WPF compilée. La déclaration d' `x:Class` sur un élément autre qu’une racine de page ou une racine d’application, ou sur un fichier XAML WPF qui n’est pas compilé, provoque une erreur au moment de la compilation dans le compilateur XAML .NET Framework 3,0 et .NET Framework 3,5 WPF. Pour plus d’informations sur les autres aspects de la gestion des `x:Class` dans WPF, consultez [code-behind et XAML dans WPF](../wpf/advanced/code-behind-and-xaml-in-wpf.md).  
  
## <a name="xclass-for-windows-workflow-foundation"></a>x :Class pour Windows Workflow Foundation  
 Par Windows Workflow Foundation, `x:Class` nomme la classe d’une activité personnalisée composée entièrement en XAML, ou nomme la classe partielle de la page XAML pour un concepteur d’activités avec code-behind.  
  
## <a name="silverlight-usage-notes"></a>Notes d'utilisation de Silverlight  
 `x:Class` pour Silverlight est documenté séparément. Pour plus d’informations, consultez [espace de noms XAML (x :) Fonctionnalités de langage (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).  
  
## <a name="see-also"></a>Voir aussi

- [x:Subclass, directive](x-subclass-directive.md)
- [XAML et classes personnalisées pour WPF](../wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier, directive](x-classmodifier-directive.md)
- [Types migrés de WPF vers System.Xaml](types-migrated-from-wpf-to-system-xaml.md)
