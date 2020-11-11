---
title: Suivi des applications .NET avec PerfCollect.
description: Un didacticiel qui vous guide dans la collecte d’une trace avec perfcollect dans .NET.
ms.topic: tutorial
ms.date: 10/23/2020
ms.openlocfilehash: 376c957833924a9991e574557671ea3c8503d7c2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507239"
---
# <a name="trace-net-applications-with-perfcollect"></a>Suivre des applications .NET avec PerfCollect

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

En cas de problèmes de performances sur Linux, la collecte d’une trace avec `perfcollect` peut être utilisée pour collecter des informations détaillées sur ce qui se passe sur l’ordinateur au moment du problème de performances.

`perfcollect` est un script bash qui tire parti de la [LTTng (tracing Tookit-Next Generation) de Linux](https://lttng.org) pour collecter des événements écrits à partir du runtime ou de n’importe quelle [EventSource](xref:System.Diagnostics.Tracing.EventListener), ainsi que des [performances](https://perf.wiki.kernel.org/) pour collecter des exemples d’UC du processus cible.

## <a name="prepare-your-machine"></a>Préparer votre ordinateur

Procédez comme suit pour préparer votre ordinateur à la collecte d’un suivi des performances avec `perfcollect` .

> [!NOTE]
> Si vous êtes dans un environnement de conteneur, votre conteneur doit avoir une `SYS_ADMIN` capacité. Pour plus d’informations sur le suivi des applications dans des conteneurs à l’aide de PerfCollect, consultez [collecter des diagnostics dans des conteneurs](./diagnostics-in-containers.md).

1. Téléchargez `perfcollect` .

    > ```bash
    > curl -OL https://aka.ms/perfcollect
    > ```

2. Rendez le script exécutable.

    > ```bash
    > chmod +x perfcollect
    > ```

3. Installer la configuration requise pour le suivi : il s’agit des bibliothèques de suivi réelles.

    > ```bash
    > sudo ./perfcollect install
    > ```

    Cette opération installe les composants requis suivants sur votre ordinateur :

    1. `perf`: le sous-système d’événements de performances Linux et l’application de collecte/visionneuse en mode utilisateur associée. `perf` fait partie de la source du noyau Linux, mais n’est généralement pas installé par défaut.

    2. `LTTng`: Utilisé pour capturer les données d’événement émises lors de l’exécution par CoreCLR. Ces données sont ensuite utilisées pour analyser le comportement de différents composants du runtime, tels que le catalogue global, le JIT et le pool de threads.

Les versions récentes de .NET Core et de l’outil de performances Linux prennent en charge la résolution automatique des noms de méthode pour le code du Framework. Si vous utilisez la version 3,1 ou une version antérieure de .NET Core, une étape supplémentaire est nécessaire. Pour plus d’informations, consultez [résolution des symboles de Framework](#resolve-framework-symbols) .

Pour résoudre les noms de méthode des dll du runtime natif (par exemple, libcoreclr.so), `perfcollect` résoudra les symboles pour eux lors de la conversion des données, mais uniquement si les symboles de ces fichiers binaires sont présents. Pour plus d’informations, consultez [obtention de symboles pour la section du runtime natif](#get-symbols-for-the-native-runtime) .

## <a name="collect-a-trace"></a>Collecter une trace

1. Deux interpréteurs de commande disponibles : un pour contrôler le suivi, désigné sous le terme **[trace]** , et l’autre pour l’exécution de l’application, appelé **[App]**.

2. **[Trace]** Démarrer la collecte.

    > ```bash
    > sudo ./perfcollect collect sampleTrace
    > ```

    Sortie attendue :

    > ```bash
    > Collection started.  Press CTRL+C to stop.
    > ```

3. **[Application]** Configurez l’interpréteur de commandes de l’application avec les variables d’environnement suivantes : cela permet la configuration du suivi de CoreCLR.

    > ```bash
    > export COMPlus_PerfMapEnabled=1
    > export COMPlus_EnableEventLog=1
    > ```

4. **[Application]** Exécutez l’application : laissez-la s’exécuter aussi longtemps que nécessaire pour capturer le problème de performances. La longueur exacte peut être aussi brève que nécessaire, à condition qu’elle capture suffisamment de temps pour que le problème de performances que vous souhaitez examiner se produise.

    > ```bash
    > dotnet run
    > ```

5. **[Trace]** Arrêter la collecte-Appuyez sur CTRL + C.

    > ```bash
    > ^C
    > ...STOPPED.
    >
    > Starting post-processing. This may take some time.
    >
    > Generating native image symbol files
    > ...SKIPPED
    > Saving native symbols
    > ...FINISHED
    > Exporting perf.data file
    > ...FINISHED
    > Compressing trace files
    > ...FINISHED
    > Cleaning up artifacts
    > ...FINISHED
    >
    > Trace saved to sampleTrace.trace.zip
    > ```

    Le fichier de trace compressé est maintenant stocké dans le répertoire de travail actuel.

## <a name="view-a-trace"></a>Afficher une trace

Il existe un certain nombre d’options pour l’affichage de la trace qui a été collectée. Les traces sont mieux affichées à l’aide de [PerfView](https://aka.ms/perfview) sur Windows, mais elles peuvent être consultées directement sur Linux à l’aide de `PerfCollect` ou de `TraceCompass` .

### <a name="use-perfcollect-to-view-the-trace-file"></a>Utiliser PerfCollect pour afficher le fichier de trace

Vous pouvez utiliser perfcollect pour afficher le suivi que vous avez collecté. Pour ce faire, utilisez la commande suivante :

```bash
./perfcollect view sampleTrace.trace.zip
```

Par défaut, cette option affiche le suivi de l’UC de l’application à l’aide de `perf` .

Pour examiner les événements collectés par le biais de `LTTng` , vous pouvez transmettre l’indicateur `-viewer lttng` pour voir les événements individuels :

```bash
./perfcollect view sampleTrace.trace.zip -viewer lttng
```

Cette opération utilise `babeltrace` la visionneuse pour imprimer la charge utile des événements :

```bash
# [01:02:18.189217659] (+0.020132603) ubuntu-xenial DotNETRuntime:ExceptionThrown_V1: { cpu_id = 0 }, { ExceptionType = "System.Exception", ExceptionMessage = "An exception happened", ExceptionEIP = 139875671834775, ExceptionHRESULT = 2148734208, ExceptionFlags = 16, ClrInstanceID = 0 }
# [01:02:18.189250227] (+0.020165171) ubuntu-xenial DotNETRuntime:ExceptionCatchStart: { cpu_id = 0 }, { EntryEIP = 139873639728404, MethodID = 139873626968120, MethodName = "void [helloworld] helloworld.Program::Main(string[])", ClrInstanceID = 0 }
```

### <a name="use-perfview-to-open-the-trace-file"></a>Utiliser PerfView pour ouvrir le fichier de trace

Pour afficher une vue agrégée de l’exemple de processeur et des événements, vous pouvez utiliser `PerfView` sur un ordinateur Windows.

1. Copiez le fichier trace.zip de Linux sur un ordinateur Windows.

2. Téléchargez PerfView à partir de <https://aka.ms/perfview> .

3. Exécuter PerfView.exe

    > ```cmd
    > PerfView.exe <path to trace.zip file>
    > ```

PerfView affiche la liste des vues prises en charge en fonction des données contenues dans le fichier de trace.

- Pour les investigations du processeur, choisissez piles de l' **UC**.

- Pour obtenir des informations détaillées sur le catalogue global, choisissez **GCStats**.

- Pour les informations JIT par processus/module/méthode, choisissez **JITStats**.

- S’il n’existe pas d’affichage pour les informations dont vous avez besoin, vous pouvez essayer de rechercher les événements dans la vue événements bruts.  Choisissez **événements**.

Pour plus d’informations sur la façon d’interpréter des affichages dans PerfView, consultez liens d’aide dans la vue elle-même, ou dans la fenêtre principale de PerfView, choisissez **aide->Guide des utilisateurs**.

### <a name="use-tracecompass-to-open-the-trace-file"></a>Utiliser TraceCompass pour ouvrir le fichier de trace

[Eclipse TraceCompass](https://www.eclipse.org/tracecompass/) est une autre option que vous pouvez utiliser pour afficher les traces. `TraceCompass` fonctionne également sur les machines Linux. vous n’avez donc pas besoin de déplacer votre suivi vers un ordinateur Windows. Pour utiliser `TraceCompass` pour ouvrir votre fichier de trace, vous devez décompresser le fichier.

```bash
unzip myTrace.trace.zip
```

`perfcollect` enregistre le suivi LTTng collecté dans un format de fichier CTF dans un sous-répertoire du `lttngTrace` . Plus précisément, le fichier CTF se trouve dans un répertoire qui ressemble à `lttngTrace/auto-20201025-101230\ust\uid\1000\64-bit\` .

Vous pouvez ouvrir le fichier de trace CTF dans `TraceCompass` en sélectionnant et en sélectionnant `File -> Open Trace` le `metadata` fichier.

Pour plus d’informations, consultez [ `TraceCompass` la documentation](https://www.eclipse.org/tracecompass/).

## <a name="resolve-framework-symbols"></a>Résoudre les symboles Framework

Les symboles de Framework doivent être générés manuellement au moment de la collecte de la trace. Elles sont différentes des symboles au niveau de l’application, car l’infrastructure est précompilée, tandis que le code de l’application est compilé juste-à-temps. Pour le code d’infrastructure qui a été précompilé en code natif, vous devez appeler `crossgen` qui sait comment générer le mappage du code natif au nom des méthodes.

`perfcollect` peut gérer la plupart des détails pour vous, mais il doit être `crossgen` disponible. Par défaut, il n’est pas installé avec la distribution .NET. Si `crossgen` n’y figure pas, `perfcollect` vous avertit et vous renvoie à ces instructions. Pour résoudre les problèmes, vous devez récupérer exactement la version appropriée de CrossGen pour le runtime que vous utilisez. Si vous placez l’outil CrossGen dans le même répertoire que les dll du Runtime .NET (par exemple, libcoreclr.so), `perfcollect` vous pouvez le trouver et ajouter les symboles d’infrastructure au fichier de trace pour vous.

Normalement, lorsque vous créez une application .NET, elle génère simplement la DLL du code que vous avez écrit, à l’aide d’une copie partagée du runtime pour le Rest.   Toutefois, vous pouvez également générer une version appelée « autonome » d’une application qui contient toutes les dll d’exécution. `crossgen` fait partie du package NuGet utilisé pour créer des applications autonomes. par conséquent, pour obtenir la version appropriée de, vous pouvez `crossgen` créer un package autonome de votre application.

Par exemple :

   >```bash
   > mkdir helloWorld
   > cd helloWorld
   > dotnet new console
   > dotnet publish --self-contained -r linux-x64
   >```

Cela crée une application Hello World et la génère comme une application autonome.

En tant qu’effet secondaire de la création de l’application autonome, l’outil dotnet télécharge un package NuGet appelé Runtime. Linux-x64. Microsoft. Netcore. app et le place dans le répertoire ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/VERSION, où VERSION correspond au numéro de version de votre Runtime .NET Core (par exemple, 2.1.0). Sous, il s’agit d’un répertoire d’outils et l’outil CrossGen dont vous avez besoin. À compter de .NET Core 3,0, l’emplacement du package est ~/.nuget/packages/microsoft.netcore.app.runtime.linux-x64/VERSION.

L' `crossgen` outil doit être placé en regard du runtime qui est réellement utilisé par votre application. En général, votre application utilise la version partagée de .NET Core qui est installée sur/usr/share/dotnet/shared/Microsoft.NETCore.App/VERSION où VERSION est le numéro de version du Runtime .NET. Il s’agit d’un emplacement partagé. vous devez donc être super utilisateur pour le modifier. Si la VERSION est 2.1.0, les commandes à mettre à jour `crossgen` sont :

   >```bash
   > sudo bash
   > cp ~/.nuget/packages/runtime.linux-x64.microsoft.netcore.app/2.1.0/tools/crossgen /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
   >```

Une fois que vous avez effectué cette opération, `perfcollect` utilise CrossGen pour inclure les symboles de Framework. L’avertissement qui a été `perfcollect` utilisé pour émettre doit disparaître. Il ne doit y avoir qu’une seule fois par ordinateur (jusqu’à ce que vous ayez mis à jour votre Runtime).

### <a name="alternative-turn-off-use-of-precompiled-code"></a>Alternative : désactiver l’utilisation du code précompilé

Si vous n’avez pas la possibilité de mettre à jour le Runtime .NET (à ajouter `crossgen` ), ou si la procédure ci-dessus ne fonctionnait pas pour une raison quelconque, il existe une autre approche pour obtenir les symboles de Framework. Vous pouvez indiquer au runtime de ne pas utiliser simplement le code d’infrastructure précompilé. Le code sera compilé juste-à-temps et `crossgen` n’est pas nécessaire.

> [!NOTE]
> Le choix de cette approche peut augmenter le temps de démarrage de votre application.

Pour ce faire, vous pouvez ajouter la variable d’environnement suivante :

```bash
export COMPlus_ZapDisable=1
```

Avec cette modification, vous devez obtenir les symboles de tout le code .NET.

## <a name="get-symbols-for-the-native-runtime"></a>Obtenir des symboles pour le runtime natif

La plupart du temps, vous êtes intéressé par votre propre code, qui est `perfcollect` résolu par défaut. Il est parfois utile de voir ce qui se passe à l’intérieur des dll .NET (ce que fait la dernière section), mais parfois ce qui se passe dans les dll du runtime natif (généralement libcoreclr.so), est intéressant.  `perfcollect` résoudra les symboles pour ceux-ci lorsqu’il convertit ses données, mais uniquement si les symboles de ces DLL natives sont présents (et sont en regard de la bibliothèque à laquelle ils sont destinés).

Il existe une commande globale appelée [dotnet-Symbol](https://github.com/dotnet/symstore/blob/master/src/dotnet-symbol/README.md#symbol-downloader-dotnet-cli-extension) qui le fait. Pour utiliser dotnet-Symbol afin d’accéder aux symboles natifs du Runtime :

1. Installez `dotnet-symbol` :

    ```bash
    dotnet tool install -g dotnet-symbol
    ```

2. Téléchargez les symboles. Si votre version installée du Runtime .NET Core est 2.1.0, la commande permettant d’effectuer cette opération est la suivante :

    ```bash
    mkdir mySymbols
    dotnet symbol --symbols --output mySymbols  /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0/lib*.so
    ```

3. Copiez les symboles à l’emplacement approprié.

    ```bash
    sudo cp mySymbols/* /usr/share/dotnet/shared/Microsoft.NETCore.App/2.1.0
    ```

    Si cela ne peut pas être fait parce que vous n’avez pas accès en écriture au répertoire approprié, vous pouvez utiliser `perf buildid-cache` pour ajouter les symboles.

Après cela, vous devez obtenir des noms symboliques pour les DLL natives lorsque vous exécutez `perfcollect` .

## <a name="collect-in-a-docker-container"></a>Collecter dans un conteneur d’ancrage

Pour plus d’informations sur l’utilisation `perfcollect` de dans les environnements de conteneur, consultez [collecter des diagnostics dans des conteneurs](./diagnostics-in-containers.md).
