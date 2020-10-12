---
title: Déployer .NET pour les fichiers binaires de fonctions définies par l’utilisateur et de Apache Spark Worker
description: Découvrez comment déployer .NET pour les fichiers binaires de fonctions de Apache Spark Worker et de fonctions définies par l’utilisateur.
ms.date: 10/09/2020
ms.topic: conceptual
ms.custom: mvc,how-to
ms.openlocfilehash: 001798bfda628ce979570bcd89e7c5553347b275
ms.sourcegitcommit: b59237ca4ec763969a0dd775a3f8f39f8c59fe24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91954956"
---
# <a name="deploy-net-for-apache-spark-worker-and-user-defined-function-binaries"></a>Déployer .NET pour les fichiers binaires de fonctions définies par l’utilisateur et de Apache Spark Worker

Cette procédure fournit des instructions générales sur le déploiement de .NET pour les fichiers binaires de fonction Apache Spark Worker et de fonction définie par l’utilisateur. Vous découvrez les variables d’environnement à configurer, ainsi que certains paramètres couramment utilisés pour lancer des applications avec `spark-submit` .

## <a name="configurations"></a>Configurations

Les configurations affichent les paramètres variables et paramètres généraux de l’environnement afin de déployer .NET pour les fichiers binaires de fonction Apache Spark Worker et définie par l’utilisateur.

### <a name="environment-variables"></a>Variables d'environnement

Lors du déploiement de Workers et de l’écriture de fonctions définies par l’utilisateur, il existe quelques variables d’environnement couramment utilisées que vous devrez peut-être définir :

| Variable d’environnement         | Description
| :--------------------------- | :----------
| DOTNET_WORKER_DIR            | Chemin d’accès où le <code>Microsoft.Spark.Worker</code> fichier binaire a été généré.</br>Elle est utilisée par le pilote Spark et sera transmise aux exécuteurs Spark. Si cette variable n’est pas configurée, les exécuteurs Spark recherchent le chemin d’accès spécifié dans la <code>PATH</code> variable d’environnement.</br>_par exemple, « C:\bin\Microsoft.Spark.Worker »_
| DOTNET_ASSEMBLY_SEARCH_PATHS | Chemins séparés par des virgules où <code>Microsoft.Spark.Worker</code> chargera les assemblys.</br>Notez que, si un chemin d’accès commence par « . », le répertoire de travail sera ajouté. En **mode fils**, « . » représente le répertoire de travail du conteneur.</br>_par exemple, « C:\Users \\ &lt; nom d’utilisateur &gt; \\ &lt; mysparkapp &gt; \bin\Debug \\ &lt; dotnet version &gt; »_
| DOTNET_WORKER_DEBUG          | Si vous souhaitez <a href="https://github.com/dotnet/spark/blob/master/docs/developer-guide.md#debugging-user-defined-function-udf">déboguer une FDU</a>, définissez cette variable d’environnement sur <code>1</code> avant d’exécuter <code>spark-submit</code> .

### <a name="parameter-options"></a>Options de paramètre
Une fois l’application Spark [regroupée](https://spark.apache.org/docs/latest/submitting-applications.html#bundling-your-applications-dependencies), vous pouvez la lancer à l’aide de `spark-submit` . Le tableau suivant présente certaines des options couramment utilisées :

| Nom du paramètre        | Description
| :---------------------| :----------
| --classe               | Point d’entrée de votre application.</br>_exemple : org. Apache. Spark. deploy. dotnet. DotnetRunner_
| --maître              | <a href="https://spark.apache.org/docs/latest/submitting-applications.html#master-urls">URL principale</a> du cluster.</br>_par exemple, fils_
| --mode de déploiement         | Si vous souhaitez déployer votre pilote sur les nœuds Worker ( <code>cluster</code> ) ou localement en tant que client externe ( <code>client</code> ).</br>Valeur par défaut : <code>client</code>
| --CONF                | Propriété de configuration Spark arbitraire au <code>key=value</code> format.</br>_par exemple, spark.yarn.appMasterEnv.DOTNET_WORKER_DIR = .\worker\Microsoft.Spark.Worker_
| --Files               | Liste de fichiers séparés par des virgules à placer dans le répertoire de travail de chaque exécuteur.<br/><ul><li>Notez que cette option s’applique uniquement au mode fils.</li><li>Il prend en charge la spécification de noms de fichiers avec # similaire à Hadoop.</br></ul>_par exemple, <code>myLocalSparkApp.dll#appSeen.dll</code> . Votre application doit utiliser le nom en tant que <code>appSeen.dll</code> référence <code>myLocalSparkApp.dll</code> lors de l’exécution sur un fil._</li>
| --Archives          | Liste d’archives séparées par des virgules à extraire dans le répertoire de travail de chaque exécuteur.</br><ul><li>Notez que cette option s’applique uniquement au mode fils.</li><li>Il prend en charge la spécification de noms de fichiers avec # similaire à Hadoop.</br></ul>_par exemple, <code>hdfs://&lt;path to your worker file&gt;/Microsoft.Spark.Worker.zip#worker</code> . Cette opération copie et extrait le fichier zip dans le <code>worker</code> dossier._</li>
| application-fichier jar       | Chemin d’accès à un fichier jar groupé incluant votre application et toutes les dépendances.</br>_par exemple, hdfs:// &lt; chemin d’accès à votre fichier jar &gt; /Microsoft-Spark- &lt; version &gt; . jar_
| arguments d’application | Arguments passés à la méthode main de votre classe principale, le cas échéant.</br>_par exemple, HDFS:// &lt; chemin d’accès à votre application application &gt; / &lt; &gt; . zip &lt; nom &gt; &lt; de votre application arguments de l’application&gt;_

> [!NOTE]
> Spécifiez tous les `--options` avant le `application-jar` lancement d’applications avec `spark-submit` , sinon elles seront ignorées. Pour plus d’informations, consultez [ `spark-submit` options](https://spark.apache.org/docs/latest/submitting-applications.html) et [exécution de Spark sur les détails du fil](https://spark.apache.org/docs/latest/running-on-yarn.html).

## <a name="frequently-asked-questions"></a>Forum aux questions
### <a name="when-i-run-a-spark-app-with-udfs-i-get-a-filenotfoundexception-error-what-should-i-do"></a>Lorsque j’exécute une application Spark avec des fonctions définies par l’utilisateur, j’obtiens une erreur « FileNotFoundException ». Que dois-je faire ?
> **Erreur :** [erreur] [TaskRunner] [0] ProcessStream () a échoué avec l’exception : System. IO. FileNotFoundException : assembly’MySparkApp, version = 1.0.0.0, culture = neutral, PublicKeyToken = null’fichier introuvable : ' mySparkApp.dll '

**Réponse :** Vérifiez que la `DOTNET_ASSEMBLY_SEARCH_PATHS` variable d’environnement est correctement définie. Il doit s’agir du chemin d’accès qui contient votre `mySparkApp.dll` .

### <a name="after-i-upgraded-my-net-for-apache-spark-version-and-reset-the-dotnet_worker_dir-environment-variable-why-do-i-still-get-the-following-ioexception-error"></a>Après la mise à niveau de mon .NET pour Apache Spark version et de la réinitialisation de la `DOTNET_WORKER_DIR` variable d’environnement, pourquoi est-ce que je reçois toujours l' `IOException` erreur suivante ?
> **Erreur :** Perte de la tâche 0,0 à l’étape 11,0 (TID 24, localhost, pilote d’exécuteur) : Java. IO. IOException : impossible d’exécuter le programme "Microsoft.Spark.Worker.exe" : CreateProcess Error = 2, le système ne peut pas trouver le fichier spécifié.

**Réponse :** Essayez de redémarrer votre fenêtre PowerShell (ou d’autres fenêtres de commande) pour qu’elle puisse prendre les dernières valeurs de variable d’environnement. Ensuite, démarrez votre programme.

### <a name="after-submitting-my-spark-application-i-get-the-error-systemtypeloadexception-could-not-load-type-systemruntimeremotingcontextscontext"></a>Après avoir envoyé mon application Spark, j’obtiens l’erreur `System.TypeLoadException: Could not load type 'System.Runtime.Remoting.Contexts.Context'` .
> **Erreur :** [erreur] [TaskRunner] [0] ProcessStream () a échoué avec l’exception : System. TypeLoadException : impossible de charger le type’System. Runtime. Remoting. contextes. Context’à partir de l’assembly’mscorlib, version = 4.0.0.0, culture = neutral, PublicKeyToken =... '.

**Réponse :** Vérifiez la `Microsoft.Spark.Worker` version que vous utilisez. Il existe deux versions : **.NET Framework 4.6.1** et **.net Core 2.1. x**. Dans ce cas, `Microsoft.Spark.Worker.net461.win-x64-<version>` (que vous pouvez [Télécharger](https://github.com/dotnet/spark/releases)) doit être utilisé, car `System.Runtime.Remoting.Contexts.Context` n’est utilisé que pour les .NET Framework.

### <a name="how-do-i-run-my-spark-application-with-udfs-on-yarn-which-environment-variables-and-parameters-should-i-use"></a>Comment faire exécuter mon application Spark avec des fonctions définies par l’utilisateur sur le fil ? Quels paramètres et variables d’environnement dois-je utiliser ?

**Réponse :** Pour lancer l’application Spark sur les fils, les variables d’environnement doivent être spécifiées en tant que `spark.yarn.appMasterEnv.[EnvironmentVariableName]` . Pour en savoir plus, voir ci-dessous `spark-submit` :

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
* [Déboguer une application .NET pour Apache Spark sur Windows](debug.md)
