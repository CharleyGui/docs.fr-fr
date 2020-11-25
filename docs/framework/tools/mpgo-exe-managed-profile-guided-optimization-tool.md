---
title: Mpgo.exe (Outil d'optimisation guidée par profil managé)
description: Utilisez Mpgo.exe, l’outil d’optimisation guidée par profil géré. Avec cet outil, optimisez les assemblys d’images natives créés par le générateur d’images natives (Ngen.exe).
ms.date: 03/30/2017
helpviewer_keywords:
- Mpgo.exe
- training scenarios, generating profiles with
- Managed Profile Guided Optimization Tool
- Ngen.exe
- Ngen.exe, profilers and native images
ms.assetid: f6976502-a000-4fbe-aaf5-a7aab9ce4ec2
ms.openlocfilehash: f8830b13cb64c737525f5399beb244aeb6d9817f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721892"
---
# <a name="mpgoexe-managed-profile-guided-optimization-tool"></a>Mpgo.exe (Outil d'optimisation guidée par profil managé)

L’outil d’optimisation guidée par profil managé (Mpgo.exe) est un outil en ligne de commande qui utilise des scénarios d’utilisateurs finaux communs afin d’optimiser les assemblys d’images natives créés par le [générateur d’images natives (Ngen.exe)](ngen-exe-native-image-generator.md). Cet outil vous permet d’exécuter les scénarios de formation qui génèrent des données de profil. Le [générateur d’images natives (Ngen.exe)](ngen-exe-native-image-generator.md) utilise ces données pour optimiser ses assemblys d’applications d’images natives générées. Un scénario de formation est une tentative d’exécution d’une utilisation prévue de votre application. Mpgo.exe est disponible dans Visual Studio Ultimate 2012 Ultimate et versions ultérieures. À partir de Visual Studio 2013, vous pouvez également utiliser Mpgo.exe pour optimiser les applications du Windows 8. x Store.

L'optimisation guidée par profil améliore le temps de démarrage de l'application, l'utilisation de la mémoire (taille de la plage de travail), et le débit en collectant les données des scénarios d'apprentissage et en les utilisant pour optimiser la disposition des images natives.

Lorsque vous rencontrez des problèmes de performance en matière de temps de démarrage et de taille de la plage de travail pour les assemblys Intermediate Language (IL), il est recommandé d'utiliser d'abord Ngen.exe pour éliminer les coûts de compilation juste-à-temps et de simplifier le partage de code. Si vous avez besoin d'autres améliorations, vous pouvez utiliser ensuite Mpgo.exe pour optimiser davantage votre application. Vous pouvez utiliser les données de performance des assemblys d'images natives non optimisés comme une référence pour évaluer les gains de performance. L'utilisation de Mpgo.exe peut entraîner des temps de démarrage à froid plus rapides et une plus petite taille de la plage de travail. Mpgo.exe ajoute des informations aux assemblys IL que Ngen.exe utilise pour créer des assemblys optimisés d'images natives. Pour plus d’informations, consultez l’entrée [Improving Launch Performance for your Desktop Applications](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/) dans le blog .NET.

Cet outil est installé automatiquement avec Visual Studio. Pour exécuter l’outil, utilisez l’invite de commandes développeur pour Visual Studio (ou l’invite de commandes Visual Studio dans Windows 7) avec les informations d’identification d’administrateur, puis tapez la commande suivante à l’invite de commandes. Pour plus d'informations, consultez [Invites de commandes](developer-command-prompt-for-vs.md).

Pour les applications de bureau :

```console
mpgo –Scenario <command> [-Import <directory>] –AssemblyList <assembly1>  <assembly2> ... -OutDir <directory> [options]
```

Pour les applications du Windows 8. x Store :

## <a name="syntax"></a>Syntaxe

```console
mpgo –Scenario <packageName> -AppID <appId> -Timeout <seconds>
```

## <a name="parameters"></a>Paramètres
 Tous les arguments à Mpgo.exe sont insensibles à la casse. Les commandes sont préfixées avec un tiret.

> [!NOTE]
> Vous pouvez utiliser `–Scenario` ou `–Import` comme commande obligatoire, mais pas les deux. Aucun des paramètres requis n'est utilisé si vous spécifiez l'option `–Reset`.

|Paramètre requis|Description|
|------------------------|-----------------|
|`-Scenario` \<*command*><br /><br /> Ou<br /><br /> `-Scenario` \<*packageName*><br /><br /> - ou -<br /><br /> `-Import` \<*directory*>|Pour les applications de bureau, utilisez `–Scenario` pour spécifier la commande qui doit exécuter l'application que vous voulez optimiser, y compris tous les arguments de ligne de commande. Utilisez trois jeux de guillemets doubles autour de la *commande* si elle spécifie un chemin qui comprend des espaces, par exemple `mpgo.exe -scenario """C:\My App\myapp.exe""" -assemblylist """C:\My App\myapp.exe""" -outdir "C:\optimized files"`. N’utilisez pas de guillemets doubles ; ils ne fonctionneront pas correctement si la *commande* inclut des espaces.<br /><br /> - ou -<br /><br /> Pour les applications du Windows 8. x Store, utilisez `–Scenario` pour spécifier le package pour lequel vous souhaitez générer des informations de profil. Si vous spécifiez le nom d'affichage du package ou le nom de famille du package au lieu du nom complet du package, Mpgo.exe sélectionnera le package qui correspond au nom que vous avez fourni s'il existe une seule correspondance. Si plusieurs packages correspondent au nom spécifié, Mpgo.exe vous invite à choisir un package.<br /><br /> Ou<br /><br /> Utilisez `-Import` pour spécifier que les données d'optimisation des assemblys précédemment optimisés doivent être utilisées pour optimiser les assemblys dans `-AssemblyList`. Le *répertoire* représente le répertoire qui contient les fichiers précédemment optimisés. Les assemblys spécifiés dans `–AssemblyList` ou `–AssemblyListFile` sont les nouvelles versions d'assemblys à optimiser à l'aide des données des fichiers importés. Utiliser des données optimisées d'une version antérieure des assemblys vous permet d'optimiser les versions plus récentes des assemblys sans réexécuter le scénario.  Toutefois, si les assemblys importés et les assemblys cibles incluent du code considérablement différent, les données d'optimisation seront inefficaces. Les noms d’assemblys spécifiés dans `–AssemblyList` ou `–AssemblyListFile` doivent être présents dans le répertoire spécifié par `–Import`*répertoire*. Utilisez trois jeux de guillemets doubles autour du *répertoire* s’il spécifie un chemin qui comprend des espaces.<br /><br /> Vous devez spécifier `–Scenario` ou `–Import`, mais pas les deux paramètres.|
|`-OutDir` \<*directory*>|Le répertoire dans lequel placer les assemblys optimisés. Si un assembly existe déjà dans le dossier de répertoire de sortie, une copie est créée et un numéro d’index est ajouté à son nom, par exemple *nom_assembly*-1.exe. Utilisez des guillemets doubles autour du *répertoire* s’il spécifie un chemin qui comprend des espaces.|
|`-AssemblyList` \<*assembly1 assembly2 ...*><br /><br /> Ou<br /><br /> `-AssemblyListFile` \<*file*>|Une liste d'assemblys (y compris les fichiers .exe et .dll), séparés par des espaces, dont vous voulez collecter des informations de profil. Vous pouvez spécifier `C:\Dir\*.dll` ou `*.dll` pour sélectionner tous les assemblys dans le répertoire de travail indiqué ou le répertoire actuel. Pour plus d'informations, consultez la section Notes.<br /><br /> Ou<br /><br /> Un fichier texte contenant la liste des assemblys dont vous souhaitez collecter les informations de profil, classée avec un assembly par ligne. Si un nom d'assembly commence par un trait d'union (-), utilisez une liste de fichiers d'assembly ou renommez l'assembly.|
|`-AppID` \<*appId*>|L'ID de l'application dans le package spécifié. Si vous utilisez le caractère générique ( \* ), Mpgo.exe essaiera d’énumérer les AppID dans le package et de revenir à \<*package_family_name*> ! Application en cas d’échec. Si vous spécifiez une chaîne qui est précédée d’un point d’exclamation (!), Mpgo.exe concatènera le nom de famille de package avec l’argument fourni.|
|`-Timeout` \<*seconds*>|Durée pendant laquelle l’application Windows 8. x Store s’exécute avant la fermeture de l’application.|

|Paramètre facultatif :|Description|
|------------------------|-----------------|
|`-64bit`|Instrumente les assemblys pour les systèmes 64 bits.  Vous devez spécifier les paramètres pour les assemblys 64 bits, même si votre assembly se déclare comme 64 bits.|
|`-ExeConfig` \<*filename*>|Spécifie le fichier de configuration que votre scénario utilise pour fournir la version et les informations du chargeur.|
|`-f`|Force l'inclusion de données de profil dans un assembly binaire, même s'il est signé.  Si l'assembly est signé, il doit être re-signé ; sinon, l'assembly ne chargera pas et ne fonctionnera pas.|
|`-Reset`|Réinitialise l'environnement pour vous assurer qu'une session de profilage abandonnée n'affecte pas vos assemblys, puis se ferme. L'environnement est réinitialisé par défaut avant et après une session de profilage.|
|`-Timeout` \<*time in seconds*>|Spécifie la durée de profilage en secondes. Utilisez une valeur qui est légèrement supérieure aux temps de démarrage observés pour les applications GUI. À la fin du délai d'attente, les données de profil sont enregistrées bien que l'application continue à fonctionner. Si vous ne définissez pas cette option, le profilage continue jusqu'à l'arrêt de l'application, et les données seront alors enregistrées.|
|`-LeaveNativeImages`|Spécifie que les images natives instrumentées ne doivent pas être supprimées après l'exécution du scénario. Cette option est principalement utilisée lorsque vous exécutez l'application que avez spécifiée pour le scénario. Cela empêchera la recréation d'images natives pour les exécutions suivantes de Mpgo.exe. Lorsque vous avez terminé d'exécuter votre application, il peut y avoir des images natives orphelines dans le cache si vous spécifiez cette option. Dans ce cas, exécutez Mpgo.exe avec le même scénario et la même liste des assemblys, et utilisez le paramètre `–RemoveNativeImages` pour supprimer ces images natives.|
|`-RemoveNativeImages`|Nettoie dans une exécution où `–LeaveNativeImages` a été spécifié. Si vous spécifiez `-RemoveNativeImages`, Mpgo.exe ignore tous les arguments sauf `-64bit` et `–AssemblyList`, et s'arrête après avoir supprimé toutes les images natives instrumentées.|

## <a name="remarks"></a>Remarques
 Vous pouvez utiliser `–AssemblyList` et `- AssemblyListFile` plusieurs fois sur la ligne de commande.

 Si vous ne spécifiez pas de chemins d'accès complets en spécifiant des assemblys, Mpgo.exe recherche dans le répertoire actif. Si vous spécifiez un chemin d'accès incorrect, Mpgo.exe affiche un message d'erreur mais continue à générer des données pour les autres assemblys. Si vous spécifiez un assembly qui n'est pas chargé pendant le scénario d'apprentissage, aucune donnée d'apprentissage n'est générée pour cet assembly.

 Si un assembly dans la liste se trouve dans le Global Assembly Cache, il ne sera pas mis à jour pour contenir les informations du profil.  Supprimez-le du Global Assembly Cache pour collecter les informations de profil.

 L'utilisation de Ngen.exe et de Mpgo.exe est recommandée uniquement pour les grandes applications managées, car l'avantage des images natives précompilées est généralement uniquement observé dans le cadre d'élimination de compilations JIT importantes au moment de l'exécution. L’exécution de Mpgo.exe sur des applications de style « Hello World » qui ne sollicitent pas trop le jeu de travail ne présente aucun avantage et Mpgo.exe peut même échouer à rassembler des données de profil.

> [!NOTE]
> Ngen.exe et Mpgo.exe ne sont pas recommandés pour les applications ASP.NET et pour les services Windows Communication Foundation (WCF).

## <a name="to-use-mpgoexe"></a>Pour utiliser Mpgo.exe

1. Utilisez un ordinateur sur lequel Visual Studio Ultimate 2012 et votre application sont installés.

2. Exécutez Mpgo.exe en tant qu'administrateur avec les paramètres nécessaires.  Consultez la section suivante pour les exemples de commande.

     Les assemblys IL (Intermediate Language) optimisés sont créés dans le dossier spécifié par le paramètre `–OutDir` (dans les exemples, il s'agit du dossier `C:\Optimized`).

3. Remplacez les assemblys IL que vous avez utilisés pour Ngen.exe par les nouveaux assemblys IL contenant les informations de profil du répertoire spécifié par `–OutDir`.

4. La configuration de l'application (à l'aide des images fournies par Mpgo.exe) installera des images natives optimisées.

## <a name="suggested-workflow"></a>Flux de travail proposé

1. Créez un jeu d'assemblys IL optimisés à l'aide de Mpgo.exe avec le paramètre `–Scenario`.

2. Vérifiez les assemblys IL optimisés dans le contrôle de code source.

3. Dans le processus de génération, appelez Mpgo.exe avec le paramètre `–Import` comme une étape après génération pour générer des images IL optimisées pour passer à Ngen.exe.

 Ce processus garantit que tous les assemblys ont des données d'optimisation. Si vous enregistrez des assemblys optimisés mis à jour (étapes 1 et 2) plus fréquemment, les nombres de performance seront plus homogènes durant le développement du produit.

## <a name="using-mpgoexe-from-visual-studio"></a>Utiliser Mpgo.exe depuis Visual Studio
 Vous pouvez exécuter Mpgo.exe depuis Visual Studio (consultez l’article [Guide pratique pour spécifier des événements de build (C#)](/visualstudio/ide/how-to-specify-build-events-csharp)) avec les restrictions suivantes :

- Vous ne pouvez pas utiliser les chemins d’accès entre guillemets avec des marques de barre oblique finales, car les macros Visual Studio utilisent également des marques de barre oblique finales par défaut. (Par exemple, `–OutDir "C:\Output Folder\"` n’est pas valide.) Pour contourner cette restriction, vous pouvez placer dans une séquence d’échappement la barre oblique finale. (Par exemple, utilisez `-OutDir "$(OutDir)\"` à la place.)

- Par défaut, Mpgo.exe n'est pas dans le chemin d'accès de build de Visual Studio. Vous devez soit ajouter le chemin d'accès à Visual Studio, soit spécifier le chemin d'accès complet sur la ligne de commande du Mpgo. Vous pouvez utiliser le paramètre `–Scenario` ou `–Import` dans l'événement après génération dans Visual Studio. Toutefois, le processus habituel consiste à utiliser `–Scenario` une seule fois à partir de l’invite de commandes développeur pour Visual Studio, puis à utiliser `–Import` pour mettre à jour les assemblys optimisés après chaque génération, par exemple : `"C:\Program Files\Microsoft Visual Studio 11.0\Team Tools\Performance Tools\mpgo.exe" -import "$(OutDir)tmp" -assemblylist "$(TargetPath)" -outdir "$(OutDir)\"`.

<a name="samples"></a>
## <a name="examples"></a>Exemples
 La commande Mpgoe.exe suivante d’une invite de commandes développeur pour Visual Studio optimise une application pour les taxes :

```console
mpgo –scenario "C:\MyApp\MyTax.exe /params par" –AssemblyList Mytax.dll MyTaxUtil2011.dll –OutDir C:\Optimized –TimeOut 15
```

 La commande Mpgo.exe suivante optimise une application pour le son :

```console
mpgo –scenario "C:\MyApp\wav2wma.exe –input song1.wav –output song1.wma" –AssemblyList transcode.dll –OutDir C:\Optimized –TimeOut 15
```

 La commande Mpgo.exe suivante utilise des données d'assemblys précédemment optimisés pour optimiser des versions plus récentes des assemblys :

```console
mpgo.exe -import "C:\Optimized" -assemblylist "C:\MyApp\MyTax.dll" "C:\MyApp\MyTaxUtil2011.dll" -outdir C:\ReOptimized
```

## <a name="see-also"></a>Voir aussi

- [Ngen.exe (générateur d’images natives)](ngen-exe-native-image-generator.md)
- [Invites de commandes](developer-command-prompt-for-vs.md)
- [Amélioration des performances de lancement pour vos applications de bureau](https://devblogs.microsoft.com/dotnet/improving-launch-performance-for-your-desktop-applications/)
- [Vue d’ensemble des améliorations des performances dans .NET Framework 4,5](/archive/msdn-magazine/2012/april/clr-an-overview-of-performance-improvements-in-net-4-5)
