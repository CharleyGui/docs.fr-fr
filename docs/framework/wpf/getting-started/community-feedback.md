---
title: Ressources de la communauté
ms.date: 03/01/2018
helpviewer_keywords:
- community resources [WPF]
- forums [WPF]
- bug descriptions [WPF]
ms.assetid: 468b060a-d54b-4900-a74a-9faccb554045
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e903045195d6f464659876334f7fedc5c695e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733811"
---
# <a name="wpf-community-feedback"></a>Commentaires de la communauté WPF

Microsoft expose une variété de ressources de la communauté pour vous permettre de découvrir, de discuter et de fournir des commentaires sur Windows Presentation Foundation (WPF). Ces ressources incluent des forums et le site de la [communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/) . Chaque ressource de la communauté offre un ensemble d’avantages différents. Ces avantages sont décrits ici, ainsi qu’un ensemble de meilleures pratiques pour l’utilisation de chacune d’elles afin de garantir la meilleure réponse de la Communauté au grand et à Microsoft en particulier.

> [!NOTE]
> N’utilisez pas la section commentaires située en bas de chaque page pour envoyer des commentaires sur les produits. Ces liens sont réservés aux commentaires sur la documentation.

## <a name="forums"></a>Forums

Le [Forum WPF](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=wpf) est la principale ressource de la communauté pour la discussion et la résolution des problèmes. Les forums facilitent la discussion et la résolution des problèmes en offrant un ensemble complet de fonctionnalités, notamment :

- la recherche ;
- le suivi de discussion ;
- la mise en forme enrichie de texte et de code ;
- Intégration Visual Studio.
- l’implication des MVP (Most Valued Professionals) et de la Communauté ;
- une surveillance visant à garantir la réponse la plus rapide aux publications.

Une autre option vous permettant de poser des questions à la communauté sur WPF est [Stack Overflow](https://stackoverflow.com/questions/tagged/wpf).

### <a name="forum-best-practices"></a>Meilleures pratiques relatives aux forums

L’utilisation des meilleures pratiques suivantes vous aide à résoudre les problèmes publiés sur le Forum WPF le plus rapidement possible. Ces pratiques s’appliquent à tous les forums.

#### <a name="search-existing-posts"></a>Rechercher des publications existantes

Certains problèmes se produisent si souvent que d’autres utilisateurs y ont déjà été confrontés avant vous. Vous pouvez donc résoudre rapidement votre problème ou apporter votre contribution à une discussion existante.

#### <a name="use-meaningful-titles"></a>Utiliser des titres explicites

Des titres concis et explicites améliorent la détectabilité de vos publications. Ils permettent également aux autres membres de la communauté de Forum WPF de déterminer plus facilement s’ils peuvent résoudre votre problème.

#### <a name="include-appropriate-content"></a>Inclure le contenu approprié

Décrivez le problème et la façon dont vous avez essayé de l’utiliser. Si possible, ajoutez des extraits de code ou un exemple très simple qui illustre le problème. Tous ces détails augmenter vos chances d’obtenir une réponse rapide à votre question.

## <a name="visual-studio-developer-community"></a>Communauté des développeurs Visual Studio

Certains problèmes peuvent parfois être difficiles, voire impossibles à résoudre. De telles situations sont liées à des bogues au niveau de la technologie, à la difficulté à appliquer la technologie à des scénarios particuliers, ou encore à un manque de prise en charge de certains scénarios particuliers. Ces informations sont importantes pour Microsoft et peuvent être fournies par le biais du site de la [communauté de développeurs Visual Studio](https://developercommunity.visualstudio.com/) .

Les éléments publiés sur le centre de commentaires sur les produits WPF sont acheminés vers la base de données de bogues interne de l’équipe WPF. Par conséquent, il s’agit de la méthode la plus fiable pour faire part de vos commentaires au propriétaire des fonctionnalités WPF. En outre, vous pouvez valider et suivre des suggestions et des bogues, ainsi que voter, ce qui aide l’équipe WPF à hiérarchiser les problèmes.

### <a name="developer-community-best-practices"></a>Meilleures pratiques pour la communauté des développeurs

Lors de la publication dans la communauté de développeurs Visual Studio, la recherche de publications existantes, la fourniture d’un titre explicite et le contenu approprié sont des pratiques recommandées importantes, tout comme pour la publication sur le Forum WPF. Vous trouverez ci-dessous d’autres pratiques à adopter.

#### <a name="search-existing-posts"></a>Rechercher des publications existantes

Certains problèmes se produisent si souvent que d’autres utilisateurs y ont déjà été confrontés avant vous. Par conséquent, vous pouvez résoudre votre problème rapidement, ou vous pouvez ajouter votre entrée à un problème existant.

#### <a name="use-meaningful-titles"></a>Utiliser des titres explicites

Des titres concis et explicites augmentent le risque que votre problème soit dirigé vers l’équipe WPF la plus appropriée dans le délai le plus court. Ceci est particulièrement important pour une technologie telle que WPF, qui contient de nombreuses fonctionnalités interdépendantes.

#### <a name="describe-how-to-reproduce-your-bug"></a>Décrire comment reproduire votre bogue

Lorsque vous publiez sur un bogue, il est important d’inclure les éléments suivants, le cas échéant :

- Fournir une description claire du bogue.
- Utiliser des extraits de code pour étayer la description du bogue.
- Fournir une liste d’étapes montrant comment reproduire le bogue.
- Inclure le plus petit exemple de code possible qui reproduit le bogue.
- Préciser si le bogue se reproduit constamment ou non.
- Inclure les informations d’exception appropriées.

 Si le bogue est lié à l’installation ou à la configuration, joignez les journaux d’installation et les captures instantanées (fichiers comportant le préfixe « dd_ » qui se trouvent dans votre dossier %temp%).

 Dans le cas de problèmes de compilation ou de génération, joignez les journaux de génération. Le système MSBuild peut être configuré pour prendre en charge la journalisation avec différents commentaires à l’aide du commutateur/v : à partir de la ligne de commande ou en configurant le niveau approprié à partir d’un environnement de développement intégré (IDE) tel que Visual Studio.

#### <a name="provide-environment-information"></a>Fournir des informations sur l’environnement

Les informations générales peuvent souvent être utiles pour ajouter du contexte à votre publication. En particulier, mentionnez la plate-forme du système d’exploitation, la famille de processeurs et l’architecture, par exemple « Windows 10 version 1709, Intel (R) Xeon (R), x64 ».

Si vous rencontrez un problème de rendu, vous devez également fournir des détails sur la carte et le pilote graphiques, si possible. Ces informations sont importantes car WPF est une infrastructure de présentation.

#### <a name="provide-solution-or-project-information"></a>Fournir des informations sur la solution ou le projet

Les bogues peuvent être liés à des outils utilisés pour développer et générer vos applications et les types d’applications que vous créez. Par conséquent, il peut être utile de spécifier :

- Le type d’application que vous générez, par exemple :
  - Application ( *. exe*) ou bibliothèque ( *. dll*)
  - Application de navigateur Extensible Application Markup Language (XBAP)
  - Application XAML libre
  - Applications autonomes installées
  - Applications autonomes déployées par ClickOnce
- L’outil de développement, par exemple :
  - MSBuild
  - Concepteur graphique d’expressions
  - Concepteur d’expression interactive
  - Visual Studio
- La configuration de la solution, par exemple :
  - Une solution
  - Un projet unique
  - Solution avec plusieurs projets dépendants
- Si votre application dispose de ressources associées ou non à un langage spécifique. Par exemple, avez-vous spécifié la propriété `UICulture` du projet ou des métadonnées localisables pour les types `Application`, `Page` et `Resource` ?
- Si vous avez utilisé le paramètre de langue neutre dans le fichier AssemblyInfo.cs ou AssemblyInfo.vb.

#### <a name="provide-scenario-and-impact-information"></a>Fournir des informations sur les scénarios et les impacts

Fournissez des informations sur le scénario qui manifeste le bogue et son impact. Ces informations sont très importantes pour l’équipe WPF lorsqu’elle décide si, quand et comment un problème doit être résolu, ou si une solution de contournement acceptable peut être utilisée à la place.

En règle générale, les scénarios de plantage et de perte de données ont un impact important et sont, par conséquent, facilement prioritaires. Certains bogues, toutefois, se produisent uniquement dans des scénarios rares, mais qui peuvent aussi parfois devenir des scénarios courants. Le fait de fournir un contexte autour du scénario et de l’impact aide l’équipe WPF à prendre la bonne décision.

## <a name="see-also"></a>Voir aussi

- [Comment signaler un problème avec Visual Studio](/visualstudio/ide/how-to-report-a-problem-with-visual-studio)
