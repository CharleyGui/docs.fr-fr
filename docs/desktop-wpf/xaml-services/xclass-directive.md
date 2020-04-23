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
ms.openlocfilehash: f589fa70c2ee1c56544fa0f0152990478aa3761f
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2020
ms.locfileid: "82072038"
---
# <a name="xclass-directive"></a>x:Class, directive
Configure la compilation de balisage XAML pour rejoindre les classes partielles entre le balisage et le code-derrière. La classe partielle de code est définie dans un fichier de code séparé dans une langue de spécification de langue commune (CLS), tandis que la classe partielle de balisage est généralement créée par génération de code pendant la compilation XAML.

## <a name="xaml-attribute-usage"></a>Utilisation d'attributs XAML

```xaml
<object x:Class="namespace.classname"...>
  ...
</object>
```

## <a name="xaml-values"></a>Valeurs XAML

|||
|-|-|
|`namespace`|facultatif. Spécifie un espace de nom CLR qui contient la classe partielle identifiée par `classname`. Si `namespace` elle est spécifiée, un `namespace` `classname`point (.) sépare et . Consultez la section Notes.|
|`classname`|Obligatoire. Spécifie le nom CLR de la classe partielle qui relie le XAML chargé et votre code-derrière pour cela XAML.|

## <a name="dependencies"></a>Les dépendances

`x:Class`ne peut être spécifié que sur l’élément racine d’une production XAML. `x:Class`est invalide sur tout objet qui a un parent dans la production XAML. Pour plus d’informations, voir [ \[MS-XAML\] Section 4.3.1.6](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

## <a name="remarks"></a>Notes

La `namespace` valeur peut contenir des points supplémentaires pour organiser des espaces de noms connexes en hiérarchies de nom, qui est une technique courante dans la programmation .NET. Seul le dernier point `x:Class` d’une série `namespace` `classname.` de valeurs est `x:Class` interprété comme séparé et La classe qui est utilisée comme ne peut pas être une classe imbriquée. Les classes imbriquées ne sont pas `x:Class` autorisées parce que la détermination de la signification des points pour les cordes est ambigu si les classes imbriquées sont autorisées.

Dans les modèles `x:Class`de `x:Class` programmation existants qui utilisent , est facultatif en ce sens qu’il est tout à fait valable d’avoir une page XAML qui n’a pas de code-derrière. Cependant, cette capacité interagit avec les actions de construction telles qu’elles sont mises en œuvre par des cadres qui utilisent XAML. `x:Class`la capacité est également influencée par les rôles que les différentes classifications de contenu spécifiés par XAML ont dans un modèle d’application et dans les actions de construction correspondantes. Si votre XAML déclare des valeurs d’attributs de gestion d’événements ou des éléments personnalisés `x:Class` instantanés où les classes de définition sont dans la classe de code-derrière, vous devez fournir la référence de directive (ou [x:Subclass](xsubclass-directive.md)) à la classe appropriée pour code-derrière.

La valeur `x:Class` de la directive doit être une chaîne qui spécifie le nom <xref:System.Type.FullName%2A?displayProperty=nameWithType>entièrement qualifié d’une classe mais sans aucune information d’assemblage (équivalente à la ). Pour des applications simples, vous pouvez omettre les informations CLR namespace si le code-derrière est également structuré de cette manière (la définition de code commence au niveau de la classe).

Le fichier de code pour une définition de page ou d’application doit être dans un fichier de code qui est inclus dans le cadre du projet qui produit une application compilée et implique la compilation de balisage. Vous devez suivre les règles de nom pour les classes CLR. Pour plus d’informations, voir [Framework Design Guidelines](../../../api/index.md). Par défaut, la classe de `public`code-derrière doit être ; cependant, vous pouvez le définir à un niveau d’accès différent en utilisant la [directive x:ClassModifier](xclassmodifier-directive.md).

Cette interprétation `x:Class` de l’attribut ne s’applique qu’à une implémentation XAML basée sur CLR, en particulier à .NET XAML Services. D’autres implémentations XAML qui ne sont pas basées sur CLR et qui n’utilisent pas .NET XAML Services peuvent utiliser une formule de résolution différente pour connecter le balisage XAML et le code de sauvegarde des temps d’exécution. Pour plus d’informations sur `x:Class`les interprétations plus générales de , voir [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).

À un certain niveau d’architecture, le sens de `x:Class` est indéfini dans .NET XAML Services. C’est parce que .NET XAML Services ne spécifie pas le modèle de programmation par lequel le balisage XAML et le code de sauvegarde sont connectés. D’autres `x:Class` utilisations de la directive pourraient être mises en œuvre par des cadres spécifiques qui utilisent des modèles de programmation ou des modèles d’application pour définir comment connecter la balisage XAML et le code-derrière basé sur CLR. Chaque cadre peut avoir ses propres actions de construction qui permettent certains des comportements ou des composants spécifiques qui doivent être inclus dans l’environnement de construction. Dans un cadre, les actions de construction peuvent également varier en fonction de la langue CLR spécifique qui est utilisée pour le code-derrière.

## <a name="xclass-in-the-wpf-programming-model"></a>x:Classe dans le modèle de programmation WPF

Dans les applications WPF et `x:Class` le modèle d’application WPF, peut être déclaré comme un attribut pour tout élément qui est la racine `Page` d’un fichier <xref:System.Windows.Application> XAML et est en cours de compilation (lorsque le XAML est inclus dans un projet d’application WPF avec l’action de construction), ou pour la racine dans la définition d’application d’une application WPF compilée. Déclarer `x:Class` sur un élément autre qu’une racine de page ou une racine d’application, ou sur un fichier WPF XAML qui n’est pas compilé, provoque une erreur de compilation de temps de compilation en vertu du compilateur .NET Framework 3.0 et .NET Framework 3.5 WPF XAML. Pour plus d’informations sur d’autres aspects du `x:Class` traitement dans WPF, voir [Code-Behind et XAML dans WPF](../../framework/wpf/advanced/code-behind-and-xaml-in-wpf.md).

## <a name="xclass-for-windows-workflow-foundation"></a>x:Classe pour Windows Workflow Foundation
Pour Windows Workflow `x:Class` Foundation, nomme la classe d’une activité personnalisée entièrement composée en XAML, ou nomme la classe partielle de la page XAML pour un concepteur d’activités avec code-derrière.

## <a name="silverlight-usage-notes"></a>Notes d’utilisation Silverlight

`x:Class`pour Silverlight est documenté séparément. Pour plus d’informations, voir [XAML Namespace (x:) Caractéristiques linguistiques (Silverlight)](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc188995(v=vs.95)).

## <a name="see-also"></a>Voir aussi

- [x:Subclass, directive](xsubclass-directive.md)
- [XAML et classes personnalisées pour WPF](../../framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)
- [x:ClassModifier, directive](xclassmodifier-directive.md)
- [Types migrés de WPF vers System.Xaml](../../framework/wpf/advanced/types-migrated-from-wpf-to-system.md)
