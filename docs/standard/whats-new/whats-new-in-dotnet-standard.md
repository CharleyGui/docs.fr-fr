---
title: Nouveautés de .NET Standard
description: Cet article résume les nouvelles fonctionnalités et améliorations de chaque nouvelle version de .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.prod: dotnet-whatsnew
ms.openlocfilehash: 299477a7375381fa7f8064562e2a68e221944a05
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817172"
---
# <a name="whats-new-in-net-standard"></a>Nouveautés de .NET Standard

.NET Standard est une spécification formelle qui définit un ensemble de versions d’API qui doivent être disponibles sur les implémentations de .NET conformes à cette version de la norme. .NET Standard est destiné aux développeurs de bibliothèques. Une bibliothèque qui cible une version .NET Standard peut être utilisée sur n’importe quelle implémentation .NET Framework, .NET Core ou Xamarin prenant en charge cette version de la norme.

.NET Standard est inclus dans le kit SDK .NET Core, ainsi que dans Visual Studio lorsque vous sélectionnez la charge de travail .NET Core.

## <a name="supported-net-implementations"></a>Implémentations de .NET prises en charge

.NET Standard 2,0 est pris en charge par les implémentations .NET suivantes :

- .NET Core 2.0 ou ultérieur
- .NET Framework 4.6.1 ou ultérieur
- Mono 5.4 ou ultérieur
- Xamarin.iOS 10.14 ou ultérieur
- Xamarin.Mac 3.8 ou ultérieur
- Xamarin.Android 8.0 ou ultérieur
- Plateforme Windows universelle 10.0.16299 ou ultérieure

## <a name="whats-new-in-net-standard-20"></a>Nouveautés de .NET Standard 2,0

.NET Standard 2,0 comprend les nouvelles fonctionnalités suivantes :

### <a name="a-vastly-expanded-set-of-apis"></a>Un ensemble d’API largement étendu

Jusqu’à la version 1,6, .NET Standard incluait un petit sous-ensemble comparatif d’API. Parmi ceux exclus, citons de nombreuses API qui étaient couramment utilisées dans .NET Framework ou Xamarin. Cela complique le développement en obligeant les développeurs à trouver des remplacements appropriés pour les API courantes lorsqu’ils développent des applications et des bibliothèques ciblant plusieurs implémentations .NET. .NET Standard 2,0 résout cette limitation en ajoutant plus de 20 000 API que celles disponibles dans .NET Standard 1,6, la version précédente du standard. Pour obtenir la liste des API qui ont été ajoutées à .NET Standard 2,0, consultez [.NET Standard 2,0 ou 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Voici certains des ajouts à l’espace de noms <xref:System> dans .NET Standard 2.0 :

- Prise en charge de la classe <xref:System.AppDomain>.
- Meilleure prise en charge de l’utilisation de tableaux provenant d’autres membres de la classe <xref:System.Array>.
- Meilleure prise en charge de l’utilisation d’attributs provenant d’autres membres de la classe <xref:System.Attribute>.
- Meilleure prise en charge du calendrier et d’autres options de mise en forme pour les valeurs <xref:System.DateTime>.
- Ajout d’une fonctionnalité d’arrondi <xref:System.Decimal>.
- Ajout d’une fonctionnalité à la classe <xref:System.Environment>.
- Meilleur contrôle du récupérateur de mémoire via la classe <xref:System.GC>.
- Meilleure prise en charge de la comparaison de chaînes, de l’énumération et de la normalisation dans la classe <xref:System.String>.
- Prise en charge des ajustements à l’heure d’été et des durées de transition dans les classes <xref:System.TimeZoneInfo.AdjustmentRule> et <xref:System.TimeZoneInfo.TransitionTime>.
- Importante amélioration de la fonctionnalité dans la classe <xref:System.Type>.
- Meilleure prise en charge de la désérialisation des objets d’exception par ajout d’un constructeur d’exception avec les paramètres <xref:System.Runtime.Serialization.SerializationInfo> et <xref:System.Runtime.Serialization.StreamingContext>.

### <a name="support-for-net-framework-libraries"></a>Prise en charge des bibliothèques .NET Framework

De nombreuses bibliothèques ciblent .NET Framework plutôt que .NET Standard. Toutefois, la plupart des appels dans ces bibliothèques sont des API qui sont incluses dans .NET Standard 2,0. À compter de .NET Standard 2,0, vous pouvez accéder aux bibliothèques de .NET Framework à partir d’une bibliothèque de .NET Standard à l’aide d’un [shim de compatibilité](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Cette couche de compatibilité est transparente pour les développeurs ; vous n’avez rien à faire pour tirer parti des bibliothèques .NET Framework.

La seule exigence est que les API appelées par la bibliothèque de classes .NET Framework doivent être incluses dans .NET Standard 2,0.

### <a name="support-for-visual-basic"></a>Prise en charge de Visual Basic

Vous pouvez désormais développer des bibliothèques .NET Standard dans Visual Basic. Visual Studio 2019 et Visual Studio 2017 version 15,3 ou ultérieure avec la charge de travail .NET Core installée incluent un modèle de bibliothèque de classes .NET Standard. Pour les développeurs Visual Basic qui utilisent d’autres outils de développement et environnements, vous pouvez utiliser la commande [dotnet new](../../core/tools/dotnet-new.md) pour créer un projet de bibliothèque .NET Standard. Pour plus d’informations, consultez [Prise en charge des outils pour les bibliothèques .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Prise en charge des outils pour les bibliothèques .NET Standard

Avec la sortie de .NET Core 2,0 et .NET Standard 2,0, Visual Studio 2017 et le [CLI .net Core](../../core/tools/index.md) incluent la prise en charge des outils pour la création de bibliothèques de .NET standard.

Si vous installez Visual Studio avec la charge de travail **développement multiplateforme .net Core** , vous pouvez créer un projet de bibliothèque .NET standard 2,0 à l’aide d’un modèle de projet, comme le montre l’illustration suivante :

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-cs.png)

Si vous utilisez le CLI .NET Core, la commande [dotnet New](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classes qui cible .NET standard 2,0 :

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-vb.png)

Si vous utilisez le CLI .NET Core, la commande [dotnet New](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classes qui cible .NET standard 2,0 :

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Voir aussi

- [.NET Standard](../net-standard.md)
- [Présentation de .NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
- [Télécharger le Kit de développement logiciel (SDK) .NET](https://dotnet.microsoft.com/download)
