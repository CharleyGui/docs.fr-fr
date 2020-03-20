---
title: Déployer .NET pour apache Spark travailleur et binaires fonction défini par l’utilisateur
description: Apprenez à déployer .NET pour apache Spark travailleur et binaires fonction défini par l’utilisateur.
ms.date: 01/21/2019
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: f373ccee398149adcadeac91f02d9896214706b0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187596"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Déployer .NET pour apache Spark travailleur et binaires fonction défini par l’utilisateur

Cette façon de fournir des instructions générales sur la façon de déployer .NET pour apache Spark travailleur et binaires fonction défini par l’utilisateur. Vous apprenez quelles variables de l’environnement à configurer, ainsi `spark-submit`que certains paramètres couramment utilisés pour lancer des applications avec .

## <a name="configurations"></a>Configurations
Les configurations affichent les variables et paramètres de l’environnement général afin de déployer .NET pour le travailleur Apache Spark et les binaires de fonction définis par l’utilisateur.

### <a name="environment-variables"></a>Variables d'environnement
Lors du déploiement des travailleurs et de l’écriture de FUD, il y a quelques variables d’environnement couramment utilisées que vous devrez peut-être définir :

| Variable d’environnement         | Description
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | Chemin où le <code>Microsoft.Spark.Worker</code> binaire a été généré.</br>Il est utilisé par le pilote Spark et sera transmis aux exécuteurs testamentaires Spark. Si cette variable n’est pas configuré, les <code>PATH</code> exécuteurs Spark rechercheront le chemin spécifié dans la variable de l’environnement.</br>_par exemple " C: 'bin’Microsoft.Spark.Worker"_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Chemins séparés par <code>Microsoft.Spark.Worker</code> la comma où chargeront les assemblages.</br>Notez que si un chemin commence par ".", le répertoire de travail sera prépendi. Si en **mode fil,**"." représenterait l’annuaire de travail du conteneur.</br>_par exemple " C:\\&lt;'Users&gt;\\&lt;nom&gt;d’utilisateur mysparkapp 'bin’Debug\\&lt;dotnet version&gt;"_
| DOTNET_WORKER_DEBUG          | Si vous voulez <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">déboguer un UDF</a>, <code>1</code> puis <code>spark-submit</code>définir cette variable d’environnement avant d’exécuter .

### <a name="parameter-options"></a>Options de paramètre
Une fois que l’application Spark est `spark-submit` [groupée,](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies)vous pouvez la lancer à l’aide de . Le tableau suivant présente quelques-unes des options couramment utilisées :

| Nom du paramètre        | Description
| :---------------------| :----------
| --classe               | Le point d’entrée de votre demande.</br>_par exemple org.apache.spark.deploy.dotnet.DotnetRunner_
| --maître              | <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">L’URL principale</a> pour le cluster.</br>_par exemple, les fils_
| --déploiement-mode         | Que ce soit pour déployer votre<code>cluster</code>chauffeur sur les nœuds du travailleur ( ) ou localement en tant que client externe (<code>client</code>).</br>Valeur par défaut : <code>client</code>
| --conf                | Propriété arbitraire de <code>key=value</code> configuration Spark en format.</br>_par exemple spark.yarn.appMasterEnv.DOTNET_WORKER_DIR._
| --fichiers               | Liste séparée par les comma des fichiers à placer dans le répertoire de travail de chaque exécuteur testamentaire.<br/><ul><li>Veuillez noter que cette option ne s’applique qu’au mode fil.</li><li>Il prend en charge la spécifier les noms de fichiers avec 'similaire à Hadoop.</br></ul>_par exemple <code>myLocalSparkApp.dll#appSeen.dll</code>. Votre application doit utiliser <code>appSeen.dll</code> le <code>myLocalSparkApp.dll</code> nom de référence lors de l’exécution sur YARN._</li>
| --archives          | Liste d’archives séparée par les comma qui sera extraite dans le répertoire de travail de chaque exécuteur testamentaire.</br><ul><li>Veuillez noter que cette option ne s’applique qu’au mode fil.</li><li>Il prend en charge la spécifier les noms de fichiers avec 'similaire à Hadoop.</br></ul>_par exemple <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code>. Cela copiera et extraira <code>worker</code> le fichier zip au dossier._</li>
| application-jar       | Chemin vers un pot groupé, y compris votre application et toutes les dépendances.</br>_par exemple, hdfs://&lt;chemin vers votre&gt;pot /microsoft-spark-version&lt;&gt;.jar_
| application-arguments | Arguments transmis à la méthode principale de votre classe principale, le cas échéant.</br>_par exemple, hdfs://&lt;chemin vers&gt;/&lt;votre&gt;application &lt;votre application&gt; &lt;.zip votre app args nom d’application&gt;_

> [!NOTE]
> Spécifiez tout le précédent `--options` `application-jar` lors du lancement des applications avec `spark-submit`, sinon ils seront ignorés. Pour plus d’informations, voir [ `spark-submit` les options](https://spark.apache.org/docs/latest/submitting-applications.html) et [l’étincelle en cours d’exécution sur les détails YARN](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Lorsque j’exécute une application d’étincelle avec des DUDF, je reçois une erreur 'FileNotFoundException'. Que dois-je faire ?
> **Erreur:** [Erreur] [TaskRunner] [0] ProcessStream () a échoué à l’exception: System.IO.FileNotFoundException: Assembly 'mySparkApp, Version '1.0.0.0, Culture’neutral, PublicKeyToken’null' fichier introuvable: 'mySparkApp.dll'

**Réponse:** Vérifiez que `DOTNET_ASSEMBLY_SEARCH_PATHS` la variable d’environnement est réglée correctement. Il devrait être le `mySparkApp.dll`chemin qui contient votre .

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Après avoir mis à niveau mon .NET `DOTNET_WORKER_DIR` pour la version Apache Spark `IOException` et réinitialiser la variable de l’environnement, pourquoi dois-je encore obtenir l’erreur suivante?
> **Erreur:** Perte de la tâche 0.0 dans l’étape 11.0 (TID 24, localhost, pilote d’exécuteur): java.io.IOException: Impossible d’exécuter le programme "Microsoft.Spark.Worker.exe": CreateProcess erreur 2, Le système ne peut pas trouver le fichier spécifié.

**Réponse:** Essayez de redémarrer votre fenêtre PowerShell (ou d’autres fenêtres de commande) d’abord afin qu’il puisse prendre les dernières valeurs variables de l’environnement. Alors commencez votre programme.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Après avoir soumis ma demande Spark, je reçois l’erreur `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'`.
> **Erreur:** [Erreur] [TaskRunner] [0] ProcessStream () a échoué à l’exception: System.TypeLoadException: Impossible de charger le type 'System.Runtime.Remoting.Contexts.Context' de l’assemblage 'mscorlib, Version '4.0.0.0, Culture’neutre, PublicKeyToken...'.

**Réponse:** Vérifiez `Microsoft.Spark.Worker` la version que vous utilisez. Il existe deux versions: **.NET Framework 4.6.1** et **.NET Core 2.1.x**. Dans ce `Microsoft.Spark.Worker.net461.win-x64-<version>` cas, (que vous pouvez `System.Runtime.Remoting.Contexts.Context` [télécharger](https://github.com/dotnet/spark/releases)) doit être utilisé depuis est seulement pour .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Comment puis-je exécuter mon application d’étincelles avec des FUD sur YARN ? Quelles variables et paramètres de l’environnement dois-je utiliser ?

**Réponse:** Pour lancer l’application d’étincelles sur YARN, les variables de l’environnement doivent être spécifiées comme `spark.yarn.appMasterEnv.[EnvironmentVariableName]`. S’il vous plaît `spark-submit`voir ci-dessous comme un exemple en utilisant:

```powershell
spark-submit \
--class org.apache.spark.deploy.dotnet.DotnetRunner \
--master yarn \
--deploy-mode cluster \
--conf spark.yarn.appMasterEnv.DOTNET_WORKER_DIR=./worker/Microsoft.Spark.Worker-<version> \
--conf spark.yarn.appMasterEnv.DOTNET_ASSEMBLY_SEARCH_PATHS=./udfs \
--archives hdfs://<path to your files>/Microsoft.Spark.Worker.net461.win-x64-<version>.zip#worker,hdfs://<path to your files>/mySparkApp.zip#udfs \
hdfs://<path to jar file>/microsoft-spark-2.4.x-<version>.jar \
hdfs://<path to your files>/mySparkApp.zip mySparkApp
```

## <a name="next-steps"></a>Étapes suivantes

* [Bien démarrer avec .NET pour Apache Spark](../tutorials/get-started.md)
* [Déboguer une application .NET pour Apache Spark sur Windows](../how-to-guides/debug.md)
