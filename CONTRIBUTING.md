---
ms.openlocfilehash: 624814e40c361c30e251a9388f1444734a276c0a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72315869"
---
# <a name="contributing"></a>Contribuer

Nous vous remercions de l’intérêt que vous portez à la documentation .NET à travers vos contributions.

> Nous transférons actuellement nos instructions dans un guide de contribution à l’échelle du site.
> Pour afficher les nouveaux conseils, consultez la [vue d’ensemble du guide du contributeur Microsoft Docs](https://docs.microsoft.com/contribute/).

Le document aborde le processus de contribution aux articles et exemples de code qui sont hébergés sur le [site de la documentation .NET](https://docs.microsoft.com/dotnet). Les contributions peuvent aller de la simple correction de fautes de frappe à la rédaction complexe de nouveaux articles.

- [Processus de contribution](#process-for-contributing)
- [L’expérience interactive C#](#the-c-interactive-experience)
- [À faire et à ne pas faire](#dos-and-donts)
- [Contrat de licence de contribution (CLA)](#contributor-license-agreement)

Ce référentiel contient la documentation conceptuelle de .NET. Le site de la documentation de .NET repose sur plusieurs référentiels en plus de celui-ci :

- [Exemples et extraits de code](https://github.com/dotnet/samples)  
    Les problèmes et les tâches de ce référentiel sont suivis dans [dotnet/docs/Problems](https://github.com/dotnet/docs/issues).
- [Informations de référence sur l’API .NET](https://github.com/dotnet/dotnet-api-docs)  
    Les problèmes et les tâches de ce référentiel sont suivis dans [dotnet/dotnet-API-docs/Problems](https://github.com/dotnet/dotnet-api-docs/issues).
- [Informations de référence sur le kit SDK .NET Compiler Platform](https://github.com/dotnet/roslyn-api-docs)  
    Les problèmes et Taks pour ce référentiel sont suivis dans [dotnet/docs/Problems](https://github.com/dotnet/docs/issues).

## <a name="process-for-contributing"></a>Processus de contribution

Vous devez avoir une connaissance élémentaire de [Git et GitHub.com](https://guides.github.com/activities/hello-world/).

**Étape 1 :** Ignorez cette étape pour les modifications mineures (par exemple, si vous corrigez une faute de frappe ou si vous ouvrez immédiatement une requête de tirage pour résoudre un problème que vous trouvez dans la documentation). Si vous souhaitez écrire un nouveau contenu ou examiner en détail un contenu existant, ouvrez un [problème](https://github.com/dotnet/docs/issues) en décrivant ce que vous voulez faire.
Le contenu situé dans le dossier *docs* est organisé en sections que l’on retrouve dans la table des matières. Définissez l’emplacement de la rubrique dans la table des matières. Obtenez des commentaires sur votre proposition.

ou

Vous pouvez également choisir des problèmes existants pour lesquels les contributions de la communauté sont les bienvenus. [Projets pour les contributeurs de la communauté .NET](https://github.com/dotnet/docs/projects/35) répertorie la plupart des éléments de travail disponibles aux contributeurs de la communauté. Selon vos centres d’intérêt et votre niveau de participation, vous pouvez choisir des problèmes dans les catégories suivantes :

- **Maintenance**. Cette catégorie inclut des contributions relativement simples, telles que la résolution de liens rompus ou incorrects, l’ajout d’exemples de code manquant, ou des problèmes liés à un contenu limité. Parfois, ces problèmes peuvent concerner un grand nombre de fichiers. Dans ce cas, vous devriez nous indiquer le contenu sur lequel vous souhaitez travailler, avant de commencer.

- **Mises à jour du contenu**. Étant donné l’énorme quantité de documents disponibles, le contenu devient facilement obsolète et nécessite une révision. En outre, pour diverses raisons, certains contenus ont été dupliqués, voire triples. La mise à jour du contenu consiste à s’assurer que des rubriques individuelles sont actualisées ou à réviser le contenu d’une zone de fonctionnalité afin d’éliminer les doublons et garantir que tout le contenu unique est conservé dans une documentation la plus restreinte possible.

- **Création de nouveau contenu**. Si vous souhaitez créer votre propre rubrique, ces problèmes répertorient les rubriques que nous aimerions ajouter à notre documentation. Veuillez nous prévenir avant de commencer à travailler sur une rubrique. Si vous souhaitez écrire une rubrique qui n’est pas répertoriée ici, ouvrez un problème.

Vous pouvez également consulter la liste de nos [problèmes ouverts](https://github.com/dotnet/docs/issues) et vous porter volontaire pour travailler sur ceux qui vous intéressent. Nous utilisons l’étiquette [up-for-grabs](https://github.com/dotnet/docs/labels/up-for-grabs) pour signaler les problèmes auxquels vous pouvez apporter votre contribution. 

**Étape 2 :** dupliquez les référentiels `dotnet/docs`, `dotnet/samples` ou `dotnet/dotnet-api-docs` si nécessaire et créez une branche pour vos modifications.

Pour les modifications mineures, vous pouvez utiliser l’interface web de GitHub. Cliquez simplement sur le bouton **Edit the file in your fork of this project** (Modifier le fichier dans la branche de ce projet) du fichier que vous souhaitez modifier. GitHub crée la nouvelle branche lorsque vous envoyez les modifications.

**Étape 3 :** appliquez les modifications sur cette nouvelle branche.

S’il s’agit d’une nouvelle rubrique, vous pouvez utiliser ce [fichier de modèle](./styleguide/template.md) comme point de départ. Il contient les recommandations rédactionnelles et explique aussi les métadonnées nécessaires pour chaque article, comme les informations sur l’auteur.

Accédez au dossier qui correspond à l’emplacement de la table des matières de votre article déterminé à l’étape 1.
Ce dossier contient les fichiers Markdown de tous les articles de la section.
Si nécessaire, créez un nouveau dossier pour y placer les fichiers de votre contenu. Le principal article de cette section s’appelle *index.md*.
Pour les images et d’autres ressources statiques, créez un sous-dossier appelé *media* dans le dossier contenant votre article, s’il n’existe pas déjà. Dans le dossier *media*, créez un sous-dossier portant le nom de l’article (sauf pour le fichier index).
Ajoutez les exemples plus volumineux au dossier *samples* à la racine du référentiel.

Veillez à respecter la syntaxe Markdown appropriée. Pour plus d’informations, consultez le [guide de style](./styleguide/template.md).

### <a name="example-structure"></a>Exemple de structure

```
docs
  /about
  /core
    /porting
      porting-overview.md
      /media
        /porting-overview
            portability_report.png
```

**Étape 4 :** Soumettez une demande de tirage (PR) de votre branche à `dotnet/docs/master`, `dotnet/dotnet-api-docs/master` ou `dotnet/samples/master`.

Votre demande de tirage doit *toujours* cibler la branche principale. Vous ne devez *jamais* ouvrir une demande de tirage qui cible la branche active.

Chaque demande de tirage devrait généralement résoudre un problème à la fois. La demande de tirage peut modifier un ou plusieurs fichiers. Si vous gérez plusieurs correctifs sur des fichiers différents, il est préférable d’utiliser des demandes de tirage distinctes.

Si votre demande de tirage répond à un problème existant, ajoutez le mot clé `Fixes #Issue_Number` au message de validation ou à la description de la demande de tirage. De cette façon, le problème est automatiquement fermé lorsque la demande de tirage est fusionnée. Pour plus d’informations, consultez [Closing issues via commit messages](https://help.github.com/articles/closing-issues-via-commit-messages/).

L’équipe .NET examine votre demande de tirage et vous fait savoir si d’autres mises à jour/modifications sont nécessaires à son approbation.

**Étape 5 :** Mettez à jour votre branche comme l’équipe vous l’y a invité.

Les personnes chargées de la maintenance fusionneront votre demande de tirage dans la branche principale une fois que les commentaires auront été appliqués et que votre modification est approuvée.

Nous envoyons (push) toutes les validations de la branche principale à la branche en ligne à une certaine fréquence. Vous pourrez voir vos contributions en ligne sur https://docs.microsoft.com/dotnet/.

### <a name="contributing-to-samples"></a>Contribution aux exemples

Nous faisons la distinction suivante pour le code existant dans notre référentiel :

- Exemples : les lecteurs peuvent télécharger et exécuter les échantillons. Tous les échantillons doivent représenter des applications ou des bibliothèques complètes. Lorsque l’échantillon crée une bibliothèque, il doit inclure des tests unitaires ou une application permettant aux lecteurs d’exécuter le code.

- Extraits de code : illustre un concept ou une tâche de moindre importance. Ils compilent mais ne sont pas destinés à être des applications complètes.

Tout le code réside dans le référentiel [dotnet/samples](https://github.com/dotnet/samples). Nous élaborons actuellement un modèle dans lequel notre structure de dossier samples correspond à notre structure de dossier docs. Voici les normes que nous appliquons :

- Le dossier *snippets* de niveau supérieur contient les extraits de code de petits échantillons ciblés.
- Les échantillons de référence d’API situés dans un dossier suivent ce modèle : *snippets/\<language>/api/\<namespace>/\<apiname>* .
- Les autres dossiers de niveau supérieur correspondent aux dossiers de niveau supérieur du référentiel *docs*. Par exemple, le référentiel docs contient un dossier *machine-learning/tutorials*, et les échantillons pour les tutoriels Machine Learning se trouvent dans le dossier *samples/machine-learning/tutorials*.

En outre, tous les échantillons dans les dossiers *core* et *standard* doivent pouvoir être créés et exécutés sur toutes les plateformes prises en charge par .NET Core. Notre système d’intégration continue appliquera cette stratégie. Le dossier *framework* de niveau supérieur contient des échantillons uniquement créés et validés sous Windows.

Nous pourrons élargir ces répertoires à mesure que le référentiel docs ajoute du nouveau contenu. Par exemple, nous ajouterons des répertoires Xamarin comme `xamarin-ios` et `xamarin-android`.

Chaque échantillon complet que vous créez doit contenir un fichier *readme.md*. Ce fichier doit contenir une brève description de l’échantillon (un ou deux paragraphes). Votre fichier *readme.md* doit indiquer aux lecteurs ce qu’ils vont apprendre en explorant cet échantillon. Le fichier *readme.md* doit également contenir un lien vers le document en direct sur le [site de documentation .NET](https://docs.microsoft.com/dotnet/welcome).
Pour déterminer si un fichier donné du référentiel pointe vers ce site, remplacez `/docs` par `https://docs.microsoft.com/dotnet` dans le chemin d’accès du référentiel.

Votre rubrique contiendra également des liens vers l’échantillon. Établissez un lien direct vers le dossier de l’échantillon sur GitHub.

Pour plus d’informations, consultez le [fichier readme des échantillons](https://github.com/dotnet/samples/blob/master/README.md).

## <a name="the-c-interactive-experience"></a>L’expérience interactive C#

De courts échantillons de code en C# peuvent utiliser la balise de langage `csharp-interactive` pour spécifier un échantillon C# qui s’exécute dans le navigateur. (Les exemples de code inline utilisent la balise `csharp-interactive`, pour les extraits de code inclus dans la source, utilisez la balise `code-csharp-interactive`.) Ces exemples de code affichent une fenêtre de code et une fenêtre de sortie dans l’article. La fenêtre de sortie affiche le résultat de l’exécution du code interactif une fois que l’utilisateur a exécuté l’échantillon. 

Le C# expérience interactive modifie comment nous collaborons avec des exemples. Les visiteurs peuvent exécuter l’échantillon pour afficher les résultats. Un certain nombre de facteurs aident à déterminer si l’échantillon ou le texte correspondant doit inclure des informations sur la sortie.

### <a name="when-to-display-the-expected-output-without-running-the-sample"></a>Quand afficher la sortie attendue sans exécuter l’échantillon

- Les articles destinés aux débutants doivent fournir une sortie permettant aux lecteurs de comparer la sortie de leur travail avec la réponse attendue.
- Les échantillons où la sortie fait partie intégrante de la rubrique doivent afficher cette sortie. Par exemple, les articles sur un texte mis en forme doivent afficher le format du texte sans exécuter l’échantillon.
- Lorsque l’échantillon et la sortie attendue sont courts, affichez plutôt la sortie. Cela permet de gagner un peu de temps.
- Les articles expliquant comment une culture actuelle ou invariante affecte la sortie doivent expliquer la sortie attendue. La fenêtre REPL (Read Evaluate Print Loop) interactive s’exécute sur un ordinateur hôte sous Linux. La culture par défaut et la culture invariante produisent une sortie différente sur divers systèmes d’exploitation et ordinateurs. L’article doit expliquer la sortie dans les systèmes Windows, Linux et Mac.

### <a name="when-to-exclude-expected-output-from-the-sample"></a>Conditions d’exclusion de la sortie attendue dans l’échantillon 

- Les articles dans lesquels l’échantillon génère une sortie plus volumineuse ne doivent pas inclure ces informations dans les commentaires. Le code est masqué une fois l’échantillon exécuté.
- Articles dans lesquels l’échantillon montre une rubrique, mais la sortie ne fait pas partie intégrante pour être comprise. Par exemple, le code exécute une requête LINQ pour expliquer la syntaxe de la requête et affiche chaque élément dans la collection en sortie.

## <a name="dos-and-donts"></a>À faire et à ne pas faire

La liste suivante montre quelques règles directrices que vous devez garder à l’esprit quand vous contribuez à la documentation .NET :

- **À ne pas faire** : Nous surprendre avec des demandes de tirage démesurées. Soumettez plutôt un problème et démarrez une discussion pour convenir avec nous de la direction à prendre avant d’investir beaucoup de votre temps.
- **À faire** : Lire le [guide de style](./styleguide/template.md) et les recommandations sur le [style et le ton](./styleguide/voice-tone.md).
- **À faire** : Utiliser le fichier de [modèle](./styleguide/template.md) comme point de départ de votre travail.
- **À faire** : Créer une branche distincte dans votre duplication (fork) avant de travailler sur les articles.
- **À faire** : Suivre le [workflow GitHub Flow](https://guides.github.com/introduction/flow/).
- **À faire** : Bloguer et tweeter (ou autre) régulièrement à propos de vos contributions.

> Note : vous remarquerez peut-être que certaines rubriques ne respectent pas toutes les recommandations spécifiées ici et dans le [guide de style](./styleguide/template.md). Nous travaillons actuellement à une cohérence globale du site. Consultez la liste des [dossiers ouverts](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Aguidelines-adherence) que nous voulons amener vers cet objectif.

## <a name="contributor-license-agreement"></a>Contrat de licence du contributeur

Vous devez signer le [contrat de licence de contribution (CLA) .NET Foundation](https://cla.dotnetfoundation.org) avant de fusionner votre demande de tirage. Vous ne devez le faire qu’une fois pour tous les projets .NET Foundation. Vous pouvez en savoir plus sur les [contrats de licence de contribution (CLA)](https://en.wikipedia.org/wiki/Contributor_License_Agreement) sur Wikipédia.

L’accord : [net-foundation-contribution-licence-agreement.pdf](https://github.com/dotnet/home/blob/master/guidance/net-foundation-contribution-license-agreement.pdf)

Vous n’êtes pas obligé de signer le contrat au préalable. Vous pouvez cloner, dupliquer (fork) et envoyer votre demande de tirage comme d’habitude. Quand votre demande de tirage est créée, elle est classifiée par un bot CLA. Si la modification est simple (par exemple, la correction d’une faute de frappe), la demande de tirage est étiquetée `cla-not-required`. Dans le cas contraire, elle est classifiée `cla-required`. Une fois que vous avez signé le contrat CLA, les demandes de tirage actuelles et futures sont étiquetées `cla-signed`.
