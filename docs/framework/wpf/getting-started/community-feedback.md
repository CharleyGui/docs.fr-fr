---
title: Commentaires de la Communauté WPF
ms.date: 03/01/2018
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6f62fbe13b42202a2eaca212236ee5fd9aa4df05
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053150"
---
# <a name="wpf-community-feedback"></a>Commentaires de la Communauté WPF

Microsoft expose une variété de ressources de communauté pour vous permettre de découvrir, de discuter et de fournir des commentaires sur Windows Presentation Foundation (WPF). Ces ressources comprennent les forums et le [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) site. Chaque ressource de la communauté offre un ensemble d’avantages différents. Ces avantages sont décrits ici, ainsi qu’un ensemble de meilleures pratiques pour l’utilisation de chacune pour garantir la meilleure réponse de la Communauté dans son ensemble et de Microsoft, en particulier.

> [!NOTE]
> N’utilisez la section Commentaires située en bas de chaque page pour envoyer des commentaires sur le produit. Ces liens sont réservés aux commentaires sur la documentation.

## <a name="forums"></a>Forums

Le [forum WPF](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=wpf) est la ressource principal de la Communauté pour discuter et de résolution des problèmes. Les forums facilitent la discussion et la résolution des problèmes en offrant un ensemble complet de fonctionnalités, notamment :

- la recherche ;
- le suivi de discussion ;
- la mise en forme enrichie de texte et de code ;
- Intégration Visual Studio.
- l’implication des MVP (Most Valued Professionals) et de la Communauté ;
- une surveillance visant à garantir la réponse la plus rapide aux publications.

Une autre option pour vous permettre de poser des questions à la Communauté sur WPF est [Stack Overflow](https://stackoverflow.com/questions/tagged/wpf).

### <a name="forum-best-practices"></a>Forum des meilleures pratiques

À l’aide des meilleures pratiques aide pour résoudre les problèmes publiés sur le forum WPF dans le plus rapidement possible. Ces pratiques s’appliquent à tous les forums.

#### <a name="search-existing-posts"></a>Rechercher des publications existantes

Certains problèmes se produisent si souvent que d’autres utilisateurs y ont déjà été confrontés avant vous. Vous pouvez donc résoudre rapidement votre problème ou apporter votre contribution à une discussion existante.

#### <a name="use-meaningful-titles"></a>Utiliser des intitulés explicites

Titres concis et explicites améliorent la détectabilité de vos publications. Elles facilitent également pour les autres membres de la Communauté forum WPF déterminer s’ils peuvent résoudre votre problème.

#### <a name="include-appropriate-content"></a>Inclure le contenu approprié

Décrivez le problème et la façon dont vous avez essayé de résoudre par son intermédiaire. Si possible, ajoutez des extraits de code ou un exemple très simple qui illustre le problème. Tous ces détails augmenter vos chances d’obtenir une réponse rapide à votre question.

## <a name="visual-studio-developer-community"></a>Communauté des développeurs Visual Studio

Certains problèmes peuvent parfois être difficiles, voire impossibles à résoudre. De telles situations sont liées à des bogues au niveau de la technologie, à la difficulté à appliquer la technologie à des scénarios particuliers, ou encore à un manque de prise en charge de certains scénarios particuliers. Ces informations est importantes de Microsoft et peut être fournies la [Visual Studio Developer Community](https://developercommunity.visualstudio.com/) site.

Les articles publiés sur le Product Feedback Center WPF sont acheminées vers la base de données de bogues interne de l’équipe WPF. Par conséquent, il est le moyen le plus fiable pour obtenir vos commentaires au propriétaire de la fonctionnalité WPF. En outre, vous pouvez valider et suivre des suggestions et des bogues ainsi voter, ce qui aide l’équipe WPF pour hiérarchiser les problèmes.

### <a name="developer-community-best-practices"></a>Meilleures pratiques de communauté de développement

Lors de la validation à la Communauté des développeurs Visual Studio, rechercher des publications existantes, fournir un intitulé explicite et de contenu approprié sont les meilleures pratiques, tout comme pour les publications sur le forum WPF. Vous trouverez ci-dessous d’autres pratiques à adopter.

#### <a name="search-existing-posts"></a>Rechercher des publications existantes

Certains problèmes se produisent si souvent que d’autres utilisateurs y ont déjà été confrontés avant vous. Par conséquent, vous pouvez résoudre rapidement votre problème, ou vous pouvez apporter votre contribution à un problème existant.

#### <a name="use-meaningful-titles"></a>Utiliser des intitulés explicites

Titres concis et explicites augmentent les chances que votre problème est dirigé vers l’équipe WPF plus approprié dans le délai le plus court. Cela est particulièrement important pour une technologie telle que WPF, qui contient de nombreuses fonctionnalités interdépendantes.

#### <a name="describe-how-to-reproduce-your-bug"></a>Expliquer comment reproduire votre bogue

Lorsque vous publiez sur un bogue, il est important d’inclure les éléments suivants, le cas échéant :

- Fournir une description claire du bogue.
- Utiliser des extraits de code pour étayer la description du bogue.
- Fournir une liste d’étapes montrant comment reproduire le bogue.
- Inclure le plus petit exemple de code possible qui reproduit le bogue.
- Préciser si le bogue se reproduit constamment ou non.
- Inclure les informations d’exception appropriées.

 Si le bogue est lié à l’installation ou à la configuration, joignez les journaux d’installation et les captures instantanées (fichiers comportant le préfixe « dd_ » qui se trouvent dans votre dossier %temp%).

 Dans le cas de problèmes de compilation ou de génération, joignez les journaux de génération. MSBuild système peut être configuré pour prend en charge l’enregistrement avec différents commentaires en utilisant le commutateur/v: de la ligne de commande ou en configurant le niveau approprié à partir d’un environnement de développement intégré (IDE) tel que Visual Studio.

#### <a name="provide-environment-information"></a>Fournir des informations sur l’environnement

Les informations générales peuvent souvent être utiles pour ajouter du contexte à votre publication. En particulier, mentionnez la plateforme de système d’exploitation, famille de processeurs et architecture, par exemple, « Windows 10 Version 1709, Intel (r) Xeon (r), x64. »

Si vous rencontrez un problème de rendu, vous devez également fournir des détails sur la carte et le pilote graphiques, si possible. Ces informations sont importantes, car WPF est une infrastructure de présentation.

#### <a name="provide-solution-or-project-information"></a>Fournir des informations de projet ou solution

Les bogues peuvent être liés à des outils utilisés pour développer et générer vos applications et les types d’applications que vous créez. Par conséquent, il peut être utile de spécifier :

- Le type d’application que vous générez, par exemple :
  - Application (*.exe*) ou bibliothèque (*.dll*)
  - Application de navigateur Extensible Application Markup Language (XAML) (XBAP)
  - Applications XAML libre
  - Applications autonomes installé
  - Applications autonomes déployées par ClickOnce
- L’outil de développement, par exemple :
  - MSBuild
  - Expression Graphic Designer
  - Expression Interactive Designer
  - Visual Studio
- La configuration de la solution, par exemple :
  - Une solution
  - Un seul projet
  - Une solution avec plusieurs projets dépendants
- Si votre application dispose de ressources associées ou non à un langage spécifique. Par exemple, avez-vous spécifié la propriété `UICulture` du projet ou des métadonnées localisables pour les types `Application`, `Page` et `Resource` ?
- Si vous avez utilisé le paramètre de langue neutre dans le fichier AssemblyInfo.cs ou AssemblyInfo.vb.

#### <a name="provide-scenario-and-impact-information"></a>Fournir des informations de scénario et l’impact

Fournissent des informations sur le scénario qui se manifeste le bogue et son impact. Ces informations sont très importantes pour l’équipe WPF lorsque celui-ci décide si, quand et comment un problème doit être résolu, ou si une solution de contournement acceptable peut être utilisée à la place.

En règle générale, les scénarios de plantage et de perte de données ont un impact important et sont, par conséquent, facilement prioritaires. Certains bogues, toutefois, se produisent uniquement dans des scénarios rares, mais qui peuvent aussi parfois devenir des scénarios courants. Fournir le contexte du scénario et l’impact aide l’équipe WPF à prendre la bonne décision.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour signaler un problème avec Visual Studio 2017](/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017)
