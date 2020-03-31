---
title: Quoi de neuf dans .NET Standard
description: Cet article résume les nouvelles fonctionnalités et améliorations de chaque nouvelle version de .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438201"
---
# <a name="whats-new-in-net-standard"></a>Quoi de neuf dans .NET Standard

.NET Standard est une spécification formelle qui définit un ensemble versionné d’API qui doivent être disponibles sur les implémentations .NET qui se conforment à cette version de la norme. .NET Standard s’adresse aux développeurs de bibliothèques. Une bibliothèque qui cible une version .NET Standard peut être utilisée sur n’importe quelle implémentation .NET Framework, .NET Core ou Xamarin prenant en charge cette version de la norme.

.NET Standard est inclus avec le .NET Core SDK, ainsi qu’avec Visual Studio lorsque vous sélectionnez la charge de travail .NET Core.

## <a name="supported-net-implementations"></a>Implémentations de .NET prises en charge

.NET Standard 2.0 est soutenu par les implémentations suivantes .NET:

- .NET Core 2.0 ou ultérieur
- .NET Framework 4.6.1 ou ultérieur
- Mono 5.4 ou ultérieur
- Xamarin.iOS 10.14 ou ultérieur
- Xamarin.Mac 3.8 ou ultérieur
- Xamarin.Android 8.0 ou ultérieur
- Plateforme Windows universelle 10.0.16299 ou ultérieure

## <a name="whats-new-in-net-standard-20"></a>Quoi de neuf dans .NET Standard 2.0

.NET Standard 2.0 comprend les nouvelles fonctionnalités suivantes:

### <a name="a-vastly-expanded-set-of-apis"></a>Un ensemble d’API largement étendu

Grâce à la version 1.6, .NET Standard comprenait un sous-ensemble relativement petit d’API. Ce sous-ensemble excluait de nombreuses API utilisées dans .NET Framework ou Xamarin. Cela complique le développement en obligeant les développeurs à trouver des remplacements appropriés pour les API courantes lorsqu’ils développent des applications et des bibliothèques ciblant plusieurs implémentations .NET. .NET Standard 2.0 répond à cette limitation en ajoutant plus de 20.000 API de plus que ce qui était disponible dans .NET Standard 1.6, la version précédente de la norme. Pour une liste des API qui ont été ajoutées à .NET Standard 2.0, voir [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

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

L’écrasante majorité des bibliothèques ciblent .NET Framework plutôt que .NET Standard. Cependant, la plupart des appels dans ces bibliothèques sont à des API qui sont inclus dans .NET Standard 2.0. En commençant par .NET Standard 2.0, vous pouvez accéder à des bibliothèques cadre .NET à partir d’une bibliothèque .NET Standard en utilisant un [cal de compatibilité](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification). Cette couche de compatibilité est transparente pour les développeurs ; vous n’avez rien à faire pour tirer parti des bibliothèques .NET Framework.

L’exigence unique est que les API appelées par la bibliothèque de classe cadre .NET doivent être incluses dans la norme .NET 2.0.

### <a name="support-for-visual-basic"></a>Prise en charge de Visual Basic

Vous pouvez désormais développer des bibliothèques .NET Standard dans Visual Basic. Visual Studio 2019 et Visual Studio 2017 version 15.3 ou plus tard avec la charge de travail .NET Core installé comprennent un modèle .NET Standard Class Library. Pour les développeurs Visual Basic qui utilisent d’autres outils de développement et environnements, vous pouvez utiliser la commande [dotnet new](../../core/tools/dotnet-new.md) pour créer un projet de bibliothèque .NET Standard. Pour plus d’informations, consultez [Prise en charge des outils pour les bibliothèques .NET Standard](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>Prise en charge des outils pour les bibliothèques .NET Standard

Avec la sortie de .NET Core 2.0 et .NET Standard 2.0, Visual Studio 2017 et le [.NET Core CLI](../../core/tools/index.md) incluent le support d’outillage pour la création de bibliothèques .NET Standard.

Si vous installez Visual Studio avec la charge de travail **de développement multiplateforme .NET Core,** vous pouvez créer un projet de bibliothèque .NET Standard 2.0 en utilisant un modèle de projet, comme le montre le chiffre suivant :

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-cs.png)

Si vous utilisez le CLI .NET Core, la nouvelle commande [dotnet](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classe qui cible .NET Standard 2.0 :

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Ajouter un nouveau projet de bibliothèque .NET Standard](./media/std-project-vb.png)

Si vous utilisez le CLI .NET Core, la nouvelle commande [dotnet](../../core/tools/dotnet-new.md) suivante crée un projet de bibliothèque de classe qui cible .NET Standard 2.0 :

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Voir aussi

- [.NET Standard](../net-standard.md)
- [Présentation de .NET Standard](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
