---
title: Porter des bibliothèques vers .NET Core
description: Découvrez comment porter des projets de bibliothèque de .NET Framework vers .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.custom: seodec18
ms.openlocfilehash: 3e3c613f6be50ae5ff2b07052c7c1bced2047855
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105286"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Porter des bibliothèques .NET Framework vers .NET Core

Découvrez comment porter du code de bibliothèque .NET Framework vers .NET Core, pour devenir multiplateforme et étendre la portée des applications qui l’utilisent.

## <a name="prerequisites"></a>Prérequis

Cet article suppose que vous :

- utilisez Visual Studio 2017 ou une version ultérieure
  - .NET Core n’est pas pris en charge dans les versions antérieures de Visual Studio
- comprenez le [processus de portage recommandé](index.md) ;
- avez résolu les problèmes des [dépendances tierces](third-party-deps.md).

Vous devez également vous familiariser avec le contenu des rubriques suivantes :

[.NET Standard](../../standard/net-standard.md)\
Cette rubrique décrit la spécification formelle des API .NET qui sont destinées à être mises à disposition sur toutes les implémentations .NET.

[Packages, métapackages et frameworks](../packages.md)   
Cet article explique comment .NET Core définit et utilise les packages et comment ceux-ci prennent en charge le code qui s’exécute sur plusieurs implémentations .NET.

[Développer des bibliothèques avec des outils multiplateformes](../tutorials/libraries.md)   
Cette rubrique explique comment écrire des bibliothèques pour .NET à l’aide d’outils CLI multiplateformes.

[Ajouts au format *csproj* pour .NET Core](../tools/csproj.md)   
Cet article décrit les modifications qui ont été apportées au fichier projet dans le cadre du passage à *csproj* et à MSBuild.

[Porter du code vers .NET Core - Analyser les dépendances tierces](third-party-deps.md)   
Cette rubrique décrit la portabilité des dépendances tierces et explique quoi faire quand une dépendance de package NuGet ne s’exécute pas sur .NET Core.

## <a name="retargeting-your-net-framework-code-to-net-framework-472"></a>Recibler du code .NET Framework vers .NET Framework 4.7.2

Si votre code ne cible pas .NET Framework 4.7.2, nous vous recommandons de le recibler vers .NET Framework 4.7.2. Cela permet de garantir la disponibilité des dernières API de remplacement pour les cas où .NET Standard ne prend pas en charge les API existantes.

Pour chacun de vos projets dans Visual Studio que vous voulez porter, procédez comme suit :

1. Cliquez avec le bouton droit sur le projet et sélectionnez **Propriétés**.
1. Dans la liste déroulante **Version cible de .NET Framework**, sélectionnez **.NET Framework 4.7.2**.
1. Recompilez vos projets.

Vos projets ciblent maintenant .NET Framework 4.7.2. Utilisez cette version de .NET Framework comme base pour le portage du code.

## <a name="determining-the-portability-of-your-code"></a>Déterminer la portabilité du code

L’étape suivante consiste à exécuter l’outil API Portability Analyzer (ApiPort) pour générer un rapport de portabilité à des fins d’analyse.

Vérifiez que vous comprenez bien [l’outil API Portability Analyzer (ApiPort)](../../standard/analyzers/portability-analyzer.md) et que vous savez générer des rapports de portabilité pour cibler .NET Core. La façon de faire est susceptible de varier selon vos besoins et vos préférences personnelles. Voici différentes approches. Vous pourrez être amené à combiner les étapes de ces approches en fonction de la structuration de votre code.

### <a name="dealing-primarily-with-the-compiler"></a>Se concentrer principalement sur le compilateur

Cette approche peut être la meilleure pour les petits projets ou les projets qui n’utilisent pas beaucoup d’API du .NET Framework. Elle est simple :

1. Exécutez ApiPort sur votre projet (facultatif). Si vous exécutez ApiPort, prenez connaissance du rapport sur les problèmes que vous devrez résoudre.
1. Recopiez tout votre code dans un nouveau projet .NET Core.
1. Pendant que vous vous référez au rapport de portabilité (s’il a été généré), résolvez les erreurs du compilateur jusqu’à ce que le projet se compile intégralement.

Bien qu’elle ne soit pas structurée, l’approche centrée sur le code permet souvent de résoudre les problèmes rapidement ; c’est peut-être la meilleure pour les projets et les bibliothèques de petite taille. Un projet contenant uniquement des modèles de données pourrait constituer un candidat idéal à cette approche.

### <a name="staying-on-the-net-framework-until-portability-issues-are-resolved"></a>Rester sur .NET Framework jusqu’à ce que les problèmes de portabilité soient résolus

Cette approche est peut-être la meilleure si vous préférez avoir du code compilable pendant tout le processus. L’approche est la suivante :

1. Exécutez ApiPort sur un projet.
1. Résolvez les problèmes en utilisant différentes API portables.
1. Notez toutes les zones où vous n’avez pas la possibilité d’utiliser une solution de rechange directe.
1. Répétez les étapes précédentes pour tous les projets à porter jusqu’à ce que vous ayez la certitude que tous sont prêts à être copiés dans un nouveau projet .NET Core.
1. Copiez le code dans un nouveau projet .NET Core.
1. Résolvez tous les problèmes pour lesquels vous avez noté qu’il n’existe pas de solution de rechange directe.

Cette approche prudente est plus structurée que celle qui consiste à résoudre simplement les erreurs de compilation, mais elle reste relativement centrée sur le code et présente l’avantage de toujours conserver du code compilable. Les moyens de résoudre les problèmes qui n’ont pas pu être traités en utilisant simplement une autre API peuvent varier considérablement. Il peut être nécessaire de développer un plan plus complet pour certains projets, ce qui est couvert par l’approche suivante.

### <a name="developing-a-comprehensive-plan-of-attack"></a>Développer un plan d’attaque complet

Cette approche est peut-être la meilleure pour les projets complexes et de grande envergure, dans lesquels il peut être nécessaire de restructurer le code ou de réécrire complètement certains passages pour prendre en charge .NET Core. L’approche est la suivante :

1. Exécutez ApiPort sur un projet.
1. Déterminez les endroits où chaque type non portable est utilisé et l’impact sur la portabilité globale.
   - Déterminez la nature de ces types. Sont-ils peu nombreux mais fréquemment utilisés ? Sont-ils nombreux mais rarement utilisés ? Leur utilisation est-elle concentrée ou est-elle répartie à travers tout le code ?
   - Est-il facile d’isoler le code non portable, afin de le traiter plus facilement ?
   - Faut-il refactoriser le code ?
   - Pour les types qui ne sont pas portables, y a-t-il des API alternatives qui accomplissent la même tâche ? Par exemple, si vous utilisez la classe <xref:System.Net.WebClient>, vous pouvez peut-être utiliser la classe <xref:System.Net.Http.HttpClient> à la place.
   - Existe-t-il d’autres API portables permettant d’accomplir une tâche, même s’il ne s’agit pas d’un remplacement immédiat ? Par exemple, si vous utilisez <xref:System.Xml.Schema.XmlSchema> pour analyser le code XML, mais que vous n’avez pas besoin de la détection de schéma XML, vous pouvez utiliser les API <xref:System.Xml.Linq> et implémenter l’analyse par vous-même, plutôt que de dépendre d’une API.
1. Si vous avez des assemblys difficiles à porter, est-il intéressant de les laisser sur le .NET Framework pour l’instant ? Voici quelques éléments à prendre en compte :
   - Certaines des fonctionnalités de votre bibliothèque pourraient ne pas être compatibles avec .NET Core, car elles dépendent trop des fonctionnalités propres à .NET Framework ou à Windows. Est-il intéressant de laisser cette fonctionnalité de côté pour l’instant et de publier une version .NET Core de votre bibliothèque avec moins de fonctionnalités à titre temporaire, jusqu’à ce que les ressources nécessaires pour porter les fonctionnalités soient disponibles ?
   - Une refactorisation serait-elle utile ?
1. Est-il raisonnable d’écrire votre propre implémentation d’une API .NET Framework non disponible ?
   Vous pouvez envisager de copier, de modifier et d’utiliser du code provenant de la [Source de référence de .NET Framework](https://github.com/Microsoft/referencesource). Le code source de référence est sous [licence du MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), ce qui vous laisse la liberté d’utiliser la source comme base pour votre propre code. Veillez simplement à mentionner correctement ce qui est propriété de Microsoft dans votre code.
1. Répétez ce processus si nécessaire pour les différents projets.
 
La phase d’analyse peut prendre un certain temps, selon la taille de votre code base. Passer du temps sur cette phase pour déterminer précisément l’étendue des modifications nécessaires et pour développer un plan fait en général gagner du temps à long terme, en particulier en cas de code base complexe.

Votre plan peut impliquer des modifications importantes de votre code base tout en continuant à cibler .NET Framework 4.7.2, ce qui en fait une version plus structurée de l’approche précédente. La mise en œuvre du plan dépend du code base.

### <a name="mixing-approaches"></a>Combiner les approches

Il est probable que vous allez combiner les approches ci-dessus de façon différente selon les projets. Vous devez faire ce qui a le plus de sens pour vous et pour votre code base.

## <a name="porting-your-tests"></a>Porter les tests

La meilleure façon de vérifier que tout fonctionne quand vous avez porté votre code est de tester votre code quand vous l’avez porté sur .NET Core. Pour cela, vous devez utiliser une infrastructure de test qui génère et exécute des tests pour .NET Core. Vous avez actuellement trois options :

- [xUnit](https://xunit.github.io/)
  - [Prise en main](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [Outil pour convertir un projet MSTest en xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Prise en main](https://github.com/nunit/docs/wiki/Installation)
  - [Billet de blog sur la migration de MSTest vers NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](https://docs.microsoft.com/visualstudio/test/unit-test-basics)

## <a name="recommended-approach-to-porting"></a>Approche recommandée du portage

En définitive, le travail de portage dépend fortement de la structuration du code .NET Framework. Il est recommandé de commencer par la *base* de la bibliothèque, qui représente la composante essentielle du code. Il peut s’agir de modèles de données ou d’autres classes et méthodes fondamentales utilisées directement ou indirectement par tout le reste.

1. Portez le projet de test qui teste la couche en cours de portage de votre bibliothèque.
1. Copiez la base de votre bibliothèque dans un nouveau projet .NET Core et sélectionnez la version de .NET Standard que vous voulez prendre en charge.
1. Apportez les modifications nécessaires pour obtenir le code à compiler. Il est possible que la plupart nécessitent l’ajout de dépendances de package NuGet à votre fichier *csproj*.
1. Exécutez les tests et procédez aux ajustements nécessaires.
1. Sélectionnez la couche suivante de code à porter et répétez les étapes précédentes.

Si vous commencez par la base de votre bibliothèque et que vous vous déplacez vers l’extérieur en testant chaque couche au fur et à mesure, le portage devient un processus systématique où les problèmes sont isolés sur une seule couche de code à la fois.

>[!div class="step-by-step"]
>[Next](project-structure.md)
