---
title: Porter des bibliothèques vers .NET Core
description: Découvrez comment porter des projets de bibliothèque de .NET Framework vers .NET Core.
author: cartermp
ms.date: 12/07/2018
ms.openlocfilehash: dcacf4d59964e0ef2009b4e9694d7f562e3a1547
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223568"
---
# <a name="port-net-framework-libraries-to-net-core"></a>Porter des bibliothèques .NET Framework vers .NET Core

Découvrez comment porter .NET Framework code de bibliothèque vers .NET Core, où il s’exécute sur plusieurs plateformes et étend la portée des applications qui l’utilisent.

## <a name="prerequisites"></a>Prérequis

Cet article suppose que vous :

- utilisez Visual Studio 2017 ou une version ultérieure (.NET Core n’est pas pris en charge dans les versions antérieures de Visual Studio.)
- comprenez le [processus de portage recommandé](index.md) ;
- avez résolu les problèmes des [dépendances tierces](third-party-deps.md).

Vous devez également vous familiariser avec le contenu des articles suivants :

[.NET Standard](../../standard/net-standard.md)\
Cet article décrit la spécification formelle des API .NET qui sont destinées à être disponibles sur toutes les implémentations de .NET.

[Développement de bibliothèques avec des outils multiplateformes](../tutorials/libraries.md)\
Cet article explique comment écrire des bibliothèques à l’aide de l’CLI .NET Core.

[Ajouts au format* csproj* pour .NET Core](../tools/csproj.md)\
Cet article décrit les modifications qui ont été apportées au fichier projet dans le cadre du passage à *csproj* et à MSBuild.

[Portage vers .NET Core-analyse de vos dépendances tierces](third-party-deps.md)\
Cet article traite de la portabilité des dépendances tierces et de ce qu’il faut faire quand une dépendance de package NuGet ne s’exécute pas sur .NET Core.

## <a name="retarget-to-net-framework-472"></a>Recibler pour .NET Framework 4.7.2

Si votre code ne cible pas .NET Framework 4.7.2, nous vous recommandons de le recibler vers .NET Framework 4.7.2. Cela garantit la disponibilité des dernières solutions API pour les cas où .NET Standard ne prend pas en charge les API existantes.

Pour chacun des projets que vous souhaitez porter, procédez comme suit dans Visual Studio :

1. Cliquez avec le bouton droit sur le projet et sélectionnez **Propriétés**.
1. Dans la liste déroulante **Version cible de .NET Framework**, sélectionnez **.NET Framework 4.7.2**.
1. Recompilez le projet.

Vos projets ciblent maintenant .NET Framework 4.7.2. Utilisez cette version de .NET Framework comme base pour le portage du code.

## <a name="determine-portability"></a>Détermination de la portabilité

L’étape suivante consiste à exécuter l’outil API Portability Analyzer (ApiPort) pour générer un rapport de portabilité à des fins d’analyse.

Vérifiez que vous comprenez bien [l’outil API Portability Analyzer (ApiPort)](../../standard/analyzers/portability-analyzer.md) et que vous savez générer des rapports de portabilité pour cibler .NET Core. La façon de faire est susceptible de varier selon vos besoins et vos préférences personnelles. Les sections suivantes décrivent quelques approches différentes. Vous pourrez être amené à combiner les étapes de ces approches en fonction de la structuration de votre code.

### <a name="deal-primarily-with-the-compiler"></a>Traitez principalement avec le compilateur

Cette approche fonctionne bien pour les petits projets ou projets qui n’utilisent pas de nombreuses API .NET Framework. Elle est simple :

1. Exécutez ApiPort sur votre projet (facultatif). Si vous exécutez ApiPort, prenez connaissance du rapport sur les problèmes que vous devrez résoudre.
1. Recopiez tout votre code dans un nouveau projet .NET Core.
1. Pendant que vous vous référez au rapport de portabilité (s’il a été généré), résolvez les erreurs du compilateur jusqu’à ce que le projet se compile intégralement.

Bien qu’elle ne soit pas structurée, cette approche axée sur le code résout souvent les problèmes rapidement. Un projet contenant uniquement des modèles de données pourrait constituer un candidat idéal à cette approche.

### <a name="stay-on-the-net-framework-until-portability-issues-are-resolved"></a>Restez sur le .NET Framework jusqu’à ce que les problèmes de portabilité soient résolus

Cette approche est peut-être la meilleure si vous préférez avoir du code compilable pendant tout le processus. L’approche est la suivante :

1. Exécutez ApiPort sur un projet.
1. Résolvez les problèmes en utilisant différentes API portables.
1. Notez toutes les zones où vous n’avez pas la possibilité d’utiliser une solution de rechange directe.
1. Répétez les étapes précédentes pour tous les projets à porter jusqu’à ce que vous ayez la certitude que tous sont prêts à être copiés dans un nouveau projet .NET Core.
1. Copiez le code dans un nouveau projet .NET Core.
1. Résolvez tous les problèmes pour lesquels vous avez noté qu’il n’existe pas de solution de rechange directe.

Cette approche prudente est plus structurée que celle qui consiste à résoudre simplement les erreurs de compilation, mais elle reste relativement centrée sur le code et présente l’avantage de toujours conserver du code compilable. Les moyens de résoudre les problèmes qui n’ont pas pu être traités en utilisant simplement une autre API peuvent varier considérablement. Vous constaterez peut-être que vous devez développer un plan plus complet pour certains projets, ce qui est abordé dans l’approche suivante.

### <a name="develop-a-comprehensive-plan-of-attack"></a>Développer un plan d’attaque complet

Cette approche est peut-être la meilleure pour les projets complexes et de grande envergure, dans lesquels il peut être nécessaire de restructurer le code ou de réécrire complètement certains passages pour prendre en charge .NET Core. L’approche est la suivante :

1. Exécutez ApiPort sur un projet.
1. Déterminez les endroits où chaque type non portable est utilisé et l’impact sur la portabilité globale.
   - Déterminez la nature de ces types. Sont-ils peu nombreux mais fréquemment utilisés ? Sont-ils nombreux mais rarement utilisés ? Leur utilisation est-elle concentrée ou est-elle répartie à travers tout le code ?
   - Est-il facile d’isoler le code non portable, afin de le traiter plus facilement ?
   - Faut-il refactoriser le code ?
   - Pour les types qui ne sont pas portables, existe-t-il des API alternatives qui accomplissent la même tâche ? Par exemple, si vous utilisez la <xref:System.Net.WebClient> classe, vous pourrez peut-être utiliser la classe à la <xref:System.Net.Http.HttpClient> place.
   - Existe-t-il d’autres API portables permettant d’accomplir une tâche, même s’il ne s’agit pas d’un remplacement immédiat ? Par exemple, si vous utilisez <xref:System.Xml.Schema.XmlSchema> pour analyser du code XML, mais que vous n’avez pas besoin de la découverte du schéma XML, vous pouvez utiliser des <xref:System.Xml.Linq> API et implémenter vous-même l’analyse au lieu de vous appuyer sur une API.
1. Si vous avez des assemblys difficiles à porter, est-il intéressant de les laisser sur le .NET Framework pour l’instant ? Voici quelques possibilités d’opérations à prendre en considération :
   - Certaines des fonctionnalités de votre bibliothèque pourraient ne pas être compatibles avec .NET Core, car elles dépendent trop des fonctionnalités propres à .NET Framework ou à Windows. Est-il intéressant de laisser cette fonctionnalité derrière pour l’instant et de publier une version .NET Core temporaire de votre bibliothèque avec moins de fonctionnalités tant que des ressources ne sont pas disponibles pour le portage des fonctionnalités ?
   - Une refactorisation serait-elle utile ?
1. Est-il raisonnable d’écrire votre propre implémentation d’une API .NET Framework non disponible ?
   Vous pouvez envisager de copier, de modifier et d’utiliser du code à partir de la [source de référence .NET Framework](https://github.com/Microsoft/referencesource). Le code source de référence est sous [licence du MIT](https://github.com/Microsoft/referencesource/blob/master/LICENSE.txt), ce qui vous laisse la liberté d’utiliser la source comme base pour votre propre code. Veillez simplement à mentionner correctement ce qui est propriété de Microsoft dans votre code.
1. Répétez ce processus si nécessaire pour les différents projets.

La phase d’analyse peut prendre un certain temps, selon la taille de votre code base. Passer du temps sur cette phase pour déterminer précisément l’étendue des modifications nécessaires et pour développer un plan fait en général gagner du temps à long terme, en particulier en cas de code base complexe.

Votre plan peut impliquer des modifications importantes de votre code base tout en continuant à cibler .NET Framework 4.7.2, ce qui en fait une version plus structurée de l’approche précédente. La mise en œuvre du plan dépend du code base.

### <a name="mixed-approach"></a>Approche mixte

Il est probable que vous allez combiner les approches ci-dessus de façon différente selon les projets. Vous devez faire ce qui a le plus de sens pour vous et pour votre code base.

## <a name="port-your-tests"></a>Portage de vos tests

La meilleure façon de vérifier que tout fonctionne quand vous avez porté votre code est de tester votre code quand vous l’avez porté sur .NET Core. Pour cela, vous devez utiliser une infrastructure de test qui génère et exécute des tests pour .NET Core. Vous avez actuellement trois options :

- [xUnit](https://xunit.github.io/)
  - [Prise en main](https://xunit.github.io/docs/getting-started-dotnet-core.html)
  - [Outil pour convertir un projet MSTest en xUnit](https://github.com/dotnet/codeformatter/tree/master/src/XUnitConverter)
- [NUnit](https://nunit.org/)
  - [Prise en main](https://github.com/nunit/docs/wiki/Installation)
  - [Billet de blog sur la migration de MSTest vers NUnit](https://www.florian-rappl.de/News/Page/275/convert-mstest-to-nunit)
- [MSTest](/visualstudio/test/unit-test-basics)

## <a name="recommended-approach"></a>Approche recommandée

En définitive, le travail de portage dépend fortement de la structuration du code .NET Framework. Une bonne façon de porter votre code est de commencer par la *base* de votre bibliothèque, qui est l’un des composants fondamentaux de votre code. Il peut s’agir de modèles de données ou d’autres classes et méthodes fondamentales utilisées directement ou indirectement par tout le reste.

1. Portez le projet de test qui teste la couche en cours de portage de votre bibliothèque.
1. Copiez la base de votre bibliothèque dans un nouveau projet .NET Core et sélectionnez la version de .NET Standard que vous souhaitez prendre en charge.
1. Apportez les modifications nécessaires pour obtenir le code à compiler. Il est possible que la plupart nécessitent l’ajout de dépendances de package NuGet à votre fichier *csproj*.
1. Exécutez les tests et procédez aux ajustements nécessaires.
1. Sélectionnez la couche suivante de code à porter et répétez les étapes précédentes.

Si vous commencez par la base de votre bibliothèque et que vous vous déplacez vers l’extérieur en testant chaque couche au fur et à mesure, le portage devient un processus systématique où les problèmes sont isolés sur une seule couche de code à la fois.

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Organiser les projets pour .NET Core](project-structure.md)
