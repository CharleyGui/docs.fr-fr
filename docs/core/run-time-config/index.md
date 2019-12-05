---
title: Configuration de l’exécution
description: Découvrez comment configurer des applications .NET Core à l’aide des paramètres de configuration de l’exécution.
ms.date: 11/13/2019
ms.openlocfilehash: 2665026347e94d26026821beb2bfcf8441f755f6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801919"
---
# <a name="net-core-run-time-configuration-settings"></a>Paramètres de configuration du Runtime .NET Core

.NET Core prend en charge l’utilisation de fichiers de configuration et de variables d’environnement pour configurer le comportement des applications .NET Core au moment de l’exécution. La configuration au moment de l’exécution est une option attrayante dans les cas suivants :

- Vous ne possédez pas ou ne contrôlez pas le code source d’une application. par conséquent, vous ne pouvez pas le configurer par programme.

- Plusieurs instances de votre application s’exécutent en même temps sur un système unique et vous souhaitez configurer chacune d’elles pour obtenir des performances optimales.

> [!NOTE]
> Cette documentation est un travail en cours. Si vous remarquez que les informations présentées ici sont incomplètes ou inexactes, vous pouvez soit [ouvrir un problème](https://github.com/dotnet/docs/issues) pour nous le faire savoir, soit [soumettre une demande de tirage](https://github.com/dotnet/docs/pulls) pour résoudre le problème. Pour plus d’informations sur l’envoi de requêtes de tirage pour le dépôt dotnet/docs, consultez le [Guide du contributeur](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).

.NET Core fournit les mécanismes suivants pour configurer des applications au moment de l’exécution :

- Le [fichier runtimeconfig. JSON](#runtimeconfigjson)

- [Variables d’environnement](#environment-variables)

Les Articles de cette section de la documentation incluent sont organisés par catégorie, par exemple, débogage et garbage collection. Le cas échéant, les options de configuration s’affichent pour *runtimeconfig. JSON* (.net Core uniquement), *app. config* (.NET Framework uniquement) et les variables d’environnement.

## <a name="runtimeconfigjson"></a>runtimeconfig. JSON

Spécifiez les options de configuration au moment de l’exécution dans la section **configProperties** du fichier *runtimeconfig. JSON* de l’application. Cette section se présente sous la forme suivante :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "config-property-name1": "config-value1",
         "config-property-name2": "config-value2"
      }
   }
}
```

Voici un exemple de fichier :

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.GC.Concurrent": true,
         "System.GC.RetainVM": true,
         "System.Threading.ThreadPool.MinThreads": "4",
         "System.Threading.ThreadPool.MaxThreads": "25"
      }
   }
}
```

Le fichier *runtimeconfig. JSON* est automatiquement créé dans le répertoire de build par la commande [dotnet Build](../tools/dotnet-build.md) . Elle est également créée lorsque vous sélectionnez l’option de menu **générer** dans Visual Studio. Vous pouvez ensuite modifier le fichier une fois qu’il a été créé.

Certaines valeurs de configuration peuvent également être définies par programmation en appelant la méthode <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>.

## <a name="environment-variables"></a>Variables d'environnement

Les variables d’environnement peuvent être utilisées pour fournir des informations de configuration au moment de l’exécution. Les boutons de configuration spécifiés en tant que variables d’environnement ont généralement le préfixe **COMPlus_** .

Vous pouvez définir des variables d’environnement à partir du panneau de configuration Windows, à partir de la ligne de commande ou par programme, en appelant la méthode <xref:System.Environment.SetEnvironmentVariable(System.String,System.String)?displayProperty=nameWithType> sur les systèmes Windows et UNIX.

Les exemples suivants montrent comment définir une variable d’environnement sur la ligne de commande :

```shell
# Windows
set COMPlus_GCRetainVM=1

# Powershell
$env:COMPlus_GCRetainVM="1"

# Unix
export COMPlus_GCRetainVM=1
```
