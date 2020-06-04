---
title: Utilisation des journaux des applications
ms.date: 07/20/2015
helpviewer_keywords:
- logs, application
- application event logs, Visual Basic
- application event logs
ms.assetid: 2581afd1-5791-4bc4-86b2-46244e9fe468
ms.openlocfilehash: e33efac8f65832c87d5c9271eba25c2ca1d1803b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387593"
---
# <a name="working-with-application-logs-in-visual-basic"></a><span data-ttu-id="d706d-102">Utilisation des journaux des applications dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d706d-102">Working with Application Logs in Visual Basic</span></span>

<span data-ttu-id="d706d-103">Les objets `My.Application.Log` et `My.Log` facilitent l’écriture des informations de journalisation et de traçage dans les journaux.</span><span class="sxs-lookup"><span data-stu-id="d706d-103">The `My.Application.Log` and `My.Log` objects make it easy to write logging and tracing information to logs.</span></span>

## <a name="how-messages-are-logged"></a><span data-ttu-id="d706d-104">Comment les messages sont enregistrés</span><span class="sxs-lookup"><span data-stu-id="d706d-104">How Messages are Logged</span></span>

<span data-ttu-id="d706d-105">Tout d’abord, la gravité du message est vérifiée avec la propriété <xref:System.Diagnostics.TraceSource.Switch%2A> de la propriété <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> du journal.</span><span class="sxs-lookup"><span data-stu-id="d706d-105">First, the severity of the message is checked with the <xref:System.Diagnostics.TraceSource.Switch%2A> property of the log's <xref:Microsoft.VisualBasic.Logging.Log.TraceSource%2A> property.</span></span> <span data-ttu-id="d706d-106">Par défaut, seuls les messages ayant une gravité de niveau « Informations » ou supérieur sont passés aux écouteurs de suivi, spécifiés dans la collection `TraceListener` du journal.</span><span class="sxs-lookup"><span data-stu-id="d706d-106">By default, only messages of severity "Information" and higher are passed on to the trace listeners, specified in the log's `TraceListener` collection.</span></span> <span data-ttu-id="d706d-107">Ensuite, chaque écouteur compare la gravité du message à la propriété <xref:System.Diagnostics.TraceSource.Switch%2A> de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="d706d-107">Then, each listener compares the severity of the message to the listener's <xref:System.Diagnostics.TraceSource.Switch%2A> property.</span></span> <span data-ttu-id="d706d-108">Si la gravité du message est suffisamment élevée, l’écouteur écrit le message.</span><span class="sxs-lookup"><span data-stu-id="d706d-108">If the message's severity is high enough, the listener writes out the message.</span></span>

<span data-ttu-id="d706d-109">Le diagramme suivant montre comment un message écrit dans la méthode `WriteEntry` est passé aux méthodes `WriteLine` des écouteurs de suivi du journal :</span><span class="sxs-lookup"><span data-stu-id="d706d-109">The following diagram shows how a message written to the `WriteEntry` method gets passed to the `WriteLine` methods of the log's trace listeners:</span></span>

![Diagramme illustrant l’appel de Mon journal.](./media/working-with-application-logs/my-log-call-messages.png)

<span data-ttu-id="d706d-111">Vous pouvez changer le comportement du journal et des écouteurs de suivi en modifiant le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="d706d-111">You can change the behavior of the log and the trace listeners by changing the application's configuration file.</span></span> <span data-ttu-id="d706d-112">Le diagramme suivant montre la correspondance entre les parties du journal et le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d706d-112">The following diagram shows the correspondence between the parts of the log and the configuration file.</span></span>

![Diagramme illustrant la configuration de Mon journal.](./media/working-with-application-logs/my-log-configuration.png)

## <a name="where-messages-are-logged"></a><span data-ttu-id="d706d-114">Emplacement d’enregistrement des messages</span><span class="sxs-lookup"><span data-stu-id="d706d-114">Where Messages are Logged</span></span>

<span data-ttu-id="d706d-115">Si l’assembly n’a pas de fichier de configuration, les objets `My.Application.Log` et `My.Log` écrivent dans la sortie de débogage de l’application (via la classe <xref:System.Diagnostics.DefaultTraceListener> ).</span><span class="sxs-lookup"><span data-stu-id="d706d-115">If the assembly has no configuration file, the `My.Application.Log` and `My.Log` objects write to the application's debug output (through the <xref:System.Diagnostics.DefaultTraceListener> class).</span></span> <span data-ttu-id="d706d-116">En outre, l’objet `My.Application.Log` écrit dans le fichier journal de l’assembly (via la classe <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> ), tandis que l’objet `My.Log` écrit dans la sortie de la page web ASP.NET (via la classe <xref:System.Web.WebPageTraceListener> ).</span><span class="sxs-lookup"><span data-stu-id="d706d-116">In addition, the `My.Application.Log` object writes to the assembly's log file (through the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener> class), while the `My.Log` object writes to the ASP.NET Web page's output (through the <xref:System.Web.WebPageTraceListener> class).</span></span>

<span data-ttu-id="d706d-117">Vous pouvez voir la sortie de débogage dans la fenêtre **Sortie** de Visual Studio lors de l’exécution de votre application en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="d706d-117">The debug output can be viewed in the Visual Studio **Output** window when running your application in debug mode.</span></span> <span data-ttu-id="d706d-118">Pour ouvrir la fenêtre **Sortie** , cliquez sur l’élément de menu **Déboguer** , pointez sur **Windows**, puis cliquez sur **Sortie**.</span><span class="sxs-lookup"><span data-stu-id="d706d-118">To open the **Output** window, click the **Debug** menu item, point to **Windows**, and then click **Output**.</span></span> <span data-ttu-id="d706d-119">Dans la fenêtre **Sortie** , sélectionnez **Déboguer** dans la zone **Afficher la sortie à partir de** .</span><span class="sxs-lookup"><span data-stu-id="d706d-119">In the **Output** window, select **Debug** from the **Show output from** box.</span></span>

<span data-ttu-id="d706d-120">Par défaut, `My.Application.Log` écrit le fichier journal dans le chemin des données d’application de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d706d-120">By default, `My.Application.Log` writes the log file in the path for the user's application data.</span></span> <span data-ttu-id="d706d-121">Vous pouvez obtenir le chemin dans la propriété <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> de l’objet <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> .</span><span class="sxs-lookup"><span data-stu-id="d706d-121">You can get the path from the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.FullLogFileName%2A> property of the <xref:Microsoft.VisualBasic.Logging.Log.DefaultFileLogWriter%2A> object.</span></span> <span data-ttu-id="d706d-122">Le format de ce chemin est le suivant :</span><span class="sxs-lookup"><span data-stu-id="d706d-122">The format of that path is as follows:</span></span>

`BasePath`\\`CompanyName`\\`ProductName`\\`ProductVersion`

<span data-ttu-id="d706d-123">Voici une valeur habituelle de `BasePath` .</span><span class="sxs-lookup"><span data-stu-id="d706d-123">A typical value for `BasePath` is as follows.</span></span>

<span data-ttu-id="d706d-124">C:\Documents and Settings\\`username`\Application Data</span><span class="sxs-lookup"><span data-stu-id="d706d-124">C:\Documents and Settings\\`username`\Application Data</span></span>

<span data-ttu-id="d706d-125">Les valeurs de `CompanyName`, de `ProductName`et de `ProductVersion` proviennent des informations d’assembly de l’application.</span><span class="sxs-lookup"><span data-stu-id="d706d-125">The values of `CompanyName`, `ProductName`, and `ProductVersion` come from the application's assembly information.</span></span> <span data-ttu-id="d706d-126">La forme du nom du fichier journal est *nom_assembly*.log, où *nom_assembly* est le nom de fichier de l’assembly sans l’extension.</span><span class="sxs-lookup"><span data-stu-id="d706d-126">The form of the log file name is *AssemblyName*.log, where *AssemblyName* is the file name of the assembly without the extension.</span></span> <span data-ttu-id="d706d-127">Si plusieurs fichiers journaux sont nécessaires, par exemple lorsque le journal d’origine n’est pas disponible lorsque l’application tente d’écrire dans le journal, le format du fichier journal est *AssemblyName* - *Iteration*. log, où `iteration` est un positif `Integer` .</span><span class="sxs-lookup"><span data-stu-id="d706d-127">If more than one log file is needed, such as when the original log is unavailable when the application attempts to write to the log, the form for the log file name is *AssemblyName*-*iteration*.log, where `iteration` is a positive `Integer`.</span></span>

<span data-ttu-id="d706d-128">Vous pouvez remplacer le comportement par défaut en ajoutant ou en modifiant les fichiers de configuration de l’ordinateur et de l’application.</span><span class="sxs-lookup"><span data-stu-id="d706d-128">You can override the default behavior by adding or changing the computer's and the application's configuration files.</span></span> <span data-ttu-id="d706d-129">Pour plus d'informations, consultez [Walkthrough: Changing Where My.Application.Log Writes Information](walkthrough-changing-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="d706d-129">For more information, see [Walkthrough: Changing Where My.Application.Log Writes Information](walkthrough-changing-where-my-application-log-writes-information.md).</span></span>

## <a name="configuring-log-settings"></a><span data-ttu-id="d706d-130">Configuration des paramètres de journalisation</span><span class="sxs-lookup"><span data-stu-id="d706d-130">Configuring Log Settings</span></span>

<span data-ttu-id="d706d-131">L' `Log` objet a une implémentation par défaut qui fonctionne sans fichier de configuration d’application, app. config. Pour modifier les valeurs par défaut, vous devez ajouter un fichier de configuration avec les nouveaux paramètres.</span><span class="sxs-lookup"><span data-stu-id="d706d-131">The `Log` object has a default implementation that works without an application configuration file, app.config. To change the defaults, you must add a configuration file with the new settings.</span></span> <span data-ttu-id="d706d-132">Pour plus d'informations, consultez [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="d706d-132">For more information, see [Walkthrough: Filtering My.Application.Log Output](walkthrough-filtering-my-application-log-output.md).</span></span>

<span data-ttu-id="d706d-133">Les sections de configuration de la journalisation se trouvent dans le nœud `<system.diagnostics>` du nœud `<configuration>` principal du fichier app.config.</span><span class="sxs-lookup"><span data-stu-id="d706d-133">The log configuration sections are located in the `<system.diagnostics>` node in the main `<configuration>` node of the app.config file.</span></span> <span data-ttu-id="d706d-134">Les informations de la journalisation sont définies dans plusieurs nœuds :</span><span class="sxs-lookup"><span data-stu-id="d706d-134">Log information is defined in several nodes:</span></span>

- <span data-ttu-id="d706d-135">Les écouteurs pour l’objet `Log` sont définis dans le nœud `<sources>` nommé DefaultSource.</span><span class="sxs-lookup"><span data-stu-id="d706d-135">The listeners for the `Log` object are defined in the `<sources>` node named DefaultSource.</span></span>

- <span data-ttu-id="d706d-136">Le filtre de gravité pour l’objet `Log` est défini dans le nœud `<switches>` nommé DefaultSwitch.</span><span class="sxs-lookup"><span data-stu-id="d706d-136">The severity filter for the `Log` object is defined in the `<switches>` node named DefaultSwitch.</span></span>

- <span data-ttu-id="d706d-137">Les écouteurs de journalisation sont définis dans le nœud `<sharedListeners>` .</span><span class="sxs-lookup"><span data-stu-id="d706d-137">The log listeners are defined in the `<sharedListeners>` node.</span></span>

 <span data-ttu-id="d706d-138">Le code suivant montre des exemples de nœuds `<sources>`, `<switches>`et `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="d706d-138">Examples of `<sources>`, `<switches>`, and `<sharedListeners>` nodes are shown in the following code:</span></span>

```xml
<configuration>
  <system.diagnostics>
    <sources>
      <source name="DefaultSource" switchName="DefaultSwitch">
        <listeners>
          <add name="FileLog"/>
        </listeners>
      </source>
    </sources>
    <switches>
      <add name="DefaultSwitch" value="Information" />
    </switches>
    <sharedListeners>
      <add name="FileLog"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
          Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
          PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL"
        initializeData="FileLogWriter"
      />
    </sharedListeners>
  </system.diagnostics>
</configuration>
```

## <a name="changing-log-settings-after-deployment"></a><span data-ttu-id="d706d-139">Modification des paramètres du journalisation après le déploiement</span><span class="sxs-lookup"><span data-stu-id="d706d-139">Changing Log Settings after Deployment</span></span>

<span data-ttu-id="d706d-140">Quand vous développez une application, ses paramètres de configuration sont stockés dans le fichier app.config, comme illustré dans les exemples ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="d706d-140">When you develop an application, its configuration settings are stored in the app.config file, as shown in the examples above.</span></span> <span data-ttu-id="d706d-141">Après avoir déployé votre application, vous pouvez toujours configurer le journal en modifiant le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d706d-141">After you deploy your application, you can still configure the log by editing the configuration file.</span></span> <span data-ttu-id="d706d-142">Dans une application Windows, le nom de ce fichier est *nom_application*.exe.config et doit se trouver dans le même dossier que le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="d706d-142">In a Windows-based application, this file's name is *applicationName*.exe.config, and it must reside in the same folder as the executable file.</span></span> <span data-ttu-id="d706d-143">Pour une application web, il s'agit du fichier Web.config associé au projet.</span><span class="sxs-lookup"><span data-stu-id="d706d-143">For a Web application, this is the Web.config file associated with the project.</span></span>

<span data-ttu-id="d706d-144">Quand votre application exécute le code qui crée une instance d’une classe pour la première fois, elle recherche des informations sur l’objet dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="d706d-144">When your application executes the code that creates an instance of a class for the first time, it checks the configuration file for information about the object.</span></span> <span data-ttu-id="d706d-145">Pour l’objet `Log` , cette action se produit lors du premier accès à cet objet `Log` .</span><span class="sxs-lookup"><span data-stu-id="d706d-145">For the `Log` object, this happens the first time the `Log` object is accessed.</span></span> <span data-ttu-id="d706d-146">Le système examine le fichier de configuration une seule fois pour un objet particulier, la première fois que votre application crée l’objet.</span><span class="sxs-lookup"><span data-stu-id="d706d-146">The system examines the configuration file only once for any particular object—the first time your application creates the object.</span></span> <span data-ttu-id="d706d-147">Par conséquent, il peut être nécessaire de redémarrer l’application pour que les modifications prennent effet.</span><span class="sxs-lookup"><span data-stu-id="d706d-147">Therefore, you may need to restart the application for the changes to take effect.</span></span>

<span data-ttu-id="d706d-148">Dans une application déployée, vous activez le traçage du code en reconfigurant les objets de commutateur avant que votre application démarre.</span><span class="sxs-lookup"><span data-stu-id="d706d-148">In a deployed application, you enable trace code by reconfiguring switch objects before your application starts.</span></span> <span data-ttu-id="d706d-149">Ceci implique généralement l’activation et la désactivation des objets de commutateur, ou le changement des niveaux de traçage, puis le redémarrage de votre application.</span><span class="sxs-lookup"><span data-stu-id="d706d-149">Typically, this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>

## <a name="security-considerations"></a><span data-ttu-id="d706d-150">Considérations relatives à la sécurité</span><span class="sxs-lookup"><span data-stu-id="d706d-150">Security Considerations</span></span>

<span data-ttu-id="d706d-151">Prenez en compte les éléments suivants lors de l’écriture de données dans le journal :</span><span class="sxs-lookup"><span data-stu-id="d706d-151">Consider the following when writing data to the log:</span></span>

- <span data-ttu-id="d706d-152">**Évitez la fuite des informations utilisateur.**</span><span class="sxs-lookup"><span data-stu-id="d706d-152">**Avoid leaking user information.**</span></span> <span data-ttu-id="d706d-153">Vérifiez que votre application écrit seulement des informations approuvées dans le journal.</span><span class="sxs-lookup"><span data-stu-id="d706d-153">Ensure that your application writes only approved information to the log.</span></span> <span data-ttu-id="d706d-154">Par exemple, il peut être acceptable que le journal de l’application contienne des noms d’utilisateurs, mais pas des mots de passe utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d706d-154">For example, it may be acceptable for the application log to contain user names, but not user passwords.</span></span>

- <span data-ttu-id="d706d-155">**Sécurisez les emplacements des journaux.**</span><span class="sxs-lookup"><span data-stu-id="d706d-155">**Make log locations secure.**</span></span> <span data-ttu-id="d706d-156">Les journaux qui contiennent des informations potentiellement sensibles doivent être stockés à un emplacement sécurisé.</span><span class="sxs-lookup"><span data-stu-id="d706d-156">Any log that contains potentially sensitive information should be stored in a secure location.</span></span>

- <span data-ttu-id="d706d-157">**Évitez les informations erronées.**</span><span class="sxs-lookup"><span data-stu-id="d706d-157">**Avoid misleading information.**</span></span> <span data-ttu-id="d706d-158">En règle générale, votre application doit valider toutes les données entrées par un utilisateur avant de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="d706d-158">In general, your application should validate all data entered by a user before using that data.</span></span> <span data-ttu-id="d706d-159">Ceci inclut l’écriture de données dans le journal de l’application.</span><span class="sxs-lookup"><span data-stu-id="d706d-159">This includes writing data to the application log.</span></span>

- <span data-ttu-id="d706d-160">**Évitez les dénis de service.**</span><span class="sxs-lookup"><span data-stu-id="d706d-160">**Avoid denial of service.**</span></span> <span data-ttu-id="d706d-161">Si votre application écrit trop d’informations dans le journal, elle peut remplir rapidement le journal ou rendre difficile la recherche d’informations importantes.</span><span class="sxs-lookup"><span data-stu-id="d706d-161">If your application writes too much information to the log, it could fill the log or make finding important information difficult.</span></span>

## <a name="see-also"></a><span data-ttu-id="d706d-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d706d-162">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="d706d-163">Enregistrement d'informations provenant de l'application</span><span class="sxs-lookup"><span data-stu-id="d706d-163">Logging Information from the Application</span></span>](index.md)
