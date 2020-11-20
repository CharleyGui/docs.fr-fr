---
title: Versions .NET, correctifs et support
description: En savoir plus sur les versions, les correctifs et la prise en charge de .NET 5 (y compris .NET Core) et versions ultérieures.
ms.date: 10/07/2020
ms.topic: overview
ms.author: tdykstra
author: tdykstra
ms.openlocfilehash: 896b88cbf1f7f31d2d26d69ec7d219da6b27ceff
ms.sourcegitcommit: 6d1ae17e60384f3b5953ca7b45ac859ec6d4c3a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2020
ms.locfileid: "94982292"
---
# <a name="releases-and-support-for-net-core-and-net-5"></a>Versions et prise en charge de .NET Core et de .NET 5

Microsoft fournit des versions majeures, des versions mineures et des mises à jour de maintenance (correctifs) pour .NET 5,0 (et .NET Core) et versions ultérieures. Cet article explique les types de version, les mises à jour de maintenance, les bandes de fonctionnalités du kit de développement logiciel, les périodes de support et les options de support.

## <a name="release-types"></a>Types de versions

Les informations sur le type de chaque version sont encodées dans le numéro de version sous la forme *major. minor. patch*.

Par exemple :

* .NET Core 3,0 et NET 5,0 sont des versions majeures.
* .NET Core 3,1 est la première version mineure après la version majeure de .NET Core 3,0.
* .NET Core 3.1.7 est le septième correctif pour .NET Core 3,1.

### <a name="major-releases"></a>Versions majeures

Les versions majeures incluent les nouvelles fonctionnalités, la surface d’exposition de l’API publique et les correctifs de bogues. Voici quelques exemples : .NET Core 3,0 et .NET 5,0.  En raison de la nature des modifications, ces versions sont supposées avoir des modifications avec rupture. Les versions majeures s’installent côte à côte avec les versions majeures précédentes.

### <a name="minor-releases"></a>Versions mineures

Les versions mineures incluent également les nouvelles fonctionnalités, la surface d’exposition de l’API publique et les correctifs de bogues, et peuvent également avoir des modifications avec rupture. Voici quelques exemples : .NET Core 2,1 et .NET Core 3,1. La différence entre ces versions et les versions majeures est que l’ampleur des modifications est plus petite. Une application effectuant une mise à niveau de .NET Core 3,0 vers 3,1 a un saut plus petit pour avancer. Les versions mineures sont installées côte à côte avec les versions mineures précédentes.

### <a name="servicing-updates"></a>Mises à jour de maintenance

Les mises à jour de maintenance (correctifs) sont fournies presque tous les mois, et ces mises à jour comportent des correctifs de sécurité et de non-sécurité. Par exemple, .NET Core 3.1.8 est la huitième mise à jour pour .NET Core 3,1. Lorsque ces mises à jour incluent des correctifs de sécurité, elles sont publiées le « patch Tuesday », qui est toujours le deuxième mardi du mois. Les mises à jour de maintenance sont censées assurer la compatibilité. À compter de .NET Core 3,1, les mises à jour de maintenance sont des mises à niveau qui suppriment la mise à jour précédente. Par exemple, la dernière mise à jour de maintenance pour 3,1 supprime la mise à jour 3,1 précédente en cas de réussite de l’installation.

### <a name="feature-bands-sdk-only"></a>Tranches de fonctionnalités (SDK uniquement)

Le contrôle de version pour le kit de développement logiciel (SDK) .NET fonctionne légèrement différemment du Runtime .NET. Pour s’aligner sur les nouvelles versions de Visual Studio, les mises à jour du kit de développement logiciel (SDK) .NET incluent parfois de nouvelles fonctionnalités ou de nouvelles versions de composants comme MSBuild et NuGet. Ces nouvelles fonctionnalités ou composants peuvent être incompatibles avec les versions fournies dans les mises à jour précédentes du kit de développement logiciel (SDK) pour la même version majeure ou mineure.

Pour différencier ces mises à jour, le kit de développement logiciel (SDK) .NET utilise le concept de bandes de fonctionnalités. Par exemple, le premier kit de développement logiciel (SDK) .NET Core 3,1 était 3.1.100. Cette version correspond au 3.1.1 XX  *Feature Band*. Les tranches de fonctionnalités sont définies dans les centaines de groupes de la troisième section du numéro de version. Par exemple, 3.1.101 et 3.1.201 sont des versions dans deux tranches de fonctionnalités différentes, tandis que 3.1.101 et 3.1.199 sont dans la même plage de fonctionnalités. Lorsque kit SDK .NET Core 3.1.101 est installé, kit SDK .NET Core 3.1.100 est supprimé de l’ordinateur s’il existe. Lorsque kit SDK .NET Core 3.1.200 est installé sur le même ordinateur, kit SDK .NET Core 3.1.101 n’est pas supprimé.

### <a name="runtime-roll-forward-and-compatibility"></a>Restauration par progression et compatibilité

Les mises à jour majeures et mineures s’installent côte à côte avec les versions précédentes. Une application conçue pour cibler une version *majeure. mineure* spécifique continue à utiliser ce Runtime ciblé même si une version plus récente est installée. L’application n’est pas automatiquement restaurée pour utiliser une version *majeure. mineure* du runtime, sauf si vous acceptez ce comportement. Une application conçue pour cibler .NET Core 3,0 ne commence pas automatiquement à s’exécuter sur .NET Core 3,1. Nous vous recommandons de reconstruire l’application et de tester les versions majeures et mineures du runtime avant le déploiement en production. Pour plus d’informations, consultez restauration par progression des [applications dépendantes](versions/selection.md#framework-dependent-apps-roll-forward) de l’infrastructure et [restauration par progression du runtime de déploiement autonome](deploying/runtime-patch-selection.md).

Les mises à jour de maintenance sont traitées différemment des versions majeures et mineures. Une application générée pour cibler .NET Core 3,1 s’exécute par défaut sur le runtime 3.1.0. Elle est automatiquement restaurée pour utiliser un nouveau Runtime 3.1.1 lorsque cette mise à jour de maintenance est installée. Ce comportement est le comportement par défaut, car nous souhaitons que les correctifs de sécurité soient utilisés dès qu’ils sont installés sans aucune autre action nécessaire. Vous pouvez vous désabonner de ce comportement de restauration par progression par défaut.

## <a name="net-core-and-net-5-version-lifecycles"></a>Cycles de vie des versions de .NET Core et .NET 5

.NET Core, .NET 5 et les versions ultérieures adoptent le [cycle de vie moderne](/lifecycle/policies/modern) plutôt que le [cycle de vie fixe](/lifecycle/policies/fixed) utilisé pour les versions de .NET Framework. Les produits avec des cycles de vie fixes offrent une longue période de support fixe, par exemple, 5 ans de support standard et 5 ans de support étendu. Le support standard inclut des correctifs de sécurité et non de sécurité, tandis que le support étendu fournit uniquement des correctifs de sécurité. Les produits qui adoptent un cycle de vie moderne ont un plus grand modèle de prise en charge des services, avec des périodes de support plus courtes et des versions plus fréquentes.

### <a name="release-tracks"></a>Suivi des versions

Il existe deux suivis de support pour les mises en production :

* Versions *actuelles*

  Ces versions sont prises en charge jusqu’à 3 mois après l’envoi de la version majeure ou mineure suivante.

  Exemple :

  * .NET Core 3,0 est fourni en septembre 2019 et a été suivi de .NET Core 3,1 en décembre 2019.
  * La prise en charge de .NET Core 3,0 s’est terminée en mars 2020, 3 mois après 3,1.

* Versions de *support à long terme* (LTS)

  Ces versions sont prises en charge pour un minimum de 3 ans, ou 1 an après la sortie de la version LTS suivante, si cette date est ultérieure.

  Exemple :

  * .NET Core 2,1 a été publié en mai 2018 et a été considéré comme une version LTS en août 2018.
  * .NET Core 3,1 était la prochaine version de LTS et a été publiée en décembre 2019.
  * Étant donné que le 2021 août (3 ans) est postérieur au 2020 décembre (un an après la publication de la version 3,1), .NET Core 2,1 est pris en charge jusqu’à la version d’août 2021.

Les mises à jour alternées entre LTS et Current, il est possible qu’une version antérieure soit prise en charge plus longtemps qu’une version ultérieure. Par exemple, .NET Core 2,1 est une version LTS avec prise en charge jusqu’au 2021 août. La version 3,0 a été expédiée plus d’un an par la suite, mais elle n’est plus prise en charge, en décembre 2019.

Les mises à jour de maintenance sont expédiées tous les mois et incluent les correctifs de sécurité et non-sécurité (fiabilité, compatibilité et stabilité). Les mises à jour de maintenance sont prises en charge jusqu’à la publication de la mise à jour de maintenance suivante. Les mises à jour de maintenance présentent le comportement de restauration par progression de l’exécution. Cela signifie que les applications s’exécutent par défaut sur la dernière mise à jour de maintenance du runtime installée.

## <a name="how-to-choose-a-release"></a>Comment choisir une version

Si vous créez un service et que vous vous attendez à poursuivre sa mise à jour régulièrement, une version actuelle telle que .NET 5,0 peut être votre meilleure option pour vous tenir informé des dernières fonctionnalités offertes par .NET.

Si vous créez une application cliente qui sera distribuée aux consommateurs, la stabilité peut être plus importante que l’accès aux fonctionnalités les plus récentes. Il se peut que votre application doive être prise en charge pendant un certain laps de temps avant que le consommateur puisse effectuer la mise à niveau vers la version suivante de l’application. Dans ce cas, une version LTS comme .NET Core 3,1 peut être l’option appropriée.

### <a name="servicing-updates"></a>Mises à jour de maintenance

Les mises à jour de maintenance .NET sont prises en charge jusqu’à la publication de la mise à jour de maintenance suivante. La cadence de publication est mensuelle.

Vous devez installer régulièrement les mises à jour de maintenance pour vous assurer que vos applications sont dans un état sécurisé et pris en charge. Par exemple, si la dernière mise à jour de maintenance pour .NET Core 3,1 est 3.1.8 et que nous livrons 3.1.9, 3.1.8 n’est plus la dernière version. Le niveau de maintenance pris en charge pour 3,1 est ensuite 3.1.9.

Pour plus d’informations sur les dernières mises à jour de maintenance pour chaque version majeure et mineure, consultez la [page téléchargements .net](https://dotnet.microsoft.com/download/dotnet-core).

## <a name="end-of-support"></a>Fin de la prise en charge

La fin du support fait référence à la date après laquelle Microsoft n’offre plus de correctifs, de mises à jour ou d’assistance technique pour une version de produit. Avant cette date, assurez-vous que vous êtes passé à en utilisant une version prise en charge. Les versions qui ne sont pas prises en charge ne reçoivent plus de mises à jour de sécurité qui protègent vos applications et vos données.

## <a name="supported-operating-systems"></a>Systèmes d’exploitation pris en charge

.NET 5 (et .NET Core) et versions ultérieures peuvent être exécutés sur une plage de systèmes d’exploitation. Chacun de ces systèmes d’exploitation a un cycle de vie défini par son organisation sponsor (par exemple, Microsoft, Red Hat ou Apple). Ces planifications de cycle de vie tiennent compte de l’ajout et de la suppression de la prise en charge des versions de système d’exploitation.

Quand une version du système d’exploitation ne prend plus en charge, nous arrêtons de tester cette version et en fournissant la prise en charge de cette version. Les utilisateurs doivent passer à une version prise en charge du système d’exploitation pour obtenir de l’aide.

Pour plus d’informations, consultez la [stratégie de cycle de vie du système d’exploitation .net](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md).

## <a name="get-support"></a>Obtenir de l’aide

Vous avez le choix entre le support assisté par Microsoft et le support de la communauté.

### <a name="microsoft-support"></a>Support Microsoft

Pour obtenir un support assisté, [Contactez un support Microsoft professionnel](https://support.microsoft.com/supportforbusiness/productselection/?sapid=4fd4947b-15ea-ce01-080f-97f2ca3c76e8).

Vous devez disposer d’un niveau de maintenance pris en charge (la dernière mise à jour de maintenance disponible) pour pouvoir bénéficier de la prise en charge. Si un système exécute 3,1 et que la mise à jour de maintenance de 3.1.8 a été publiée, 3.1.8 doit être installé en tant que première étape.

### <a name="community-support"></a>Support de la communauté pour les objets blob

Pour obtenir un support technique de la Communauté, consultez la [page Communauté](https://dotnet.microsoft.com/platform/community).

## <a name="see-also"></a>Voir aussi

Pour plus d’informations, y compris des plages de dates prises en charge pour chaque version de .NET Core et pour .NET 5, consultez la [stratégie de support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).
