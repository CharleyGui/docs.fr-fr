---
title: filtrage de la sortie de My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Log object, filtering output
- My.Application.Log object, filtering output
- application event logs, output filtering
ms.assetid: 2c0a457a-38a4-49e1-934d-a51320b7b4ca
ms.openlocfilehash: f18556bbe1ca2d77925482319246d403892d31ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353588"
---
# <a name="walkthrough-filtering-myapplicationlog-output-visual-basic"></a><span data-ttu-id="7f36a-102">Procédure pas à pas : filtrage de la sortie de My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f36a-102">Walkthrough: Filtering My.Application.Log Output (Visual Basic)</span></span>

<span data-ttu-id="7f36a-103">Cette procédure pas à pas montre comment modifier le filtrage de journal par défaut de l’objet `My.Application.Log` pour contrôler les informations passées de l’objet `Log` aux écouteurs et celles qui sont écrites par les écouteurs.</span><span class="sxs-lookup"><span data-stu-id="7f36a-103">This walkthrough demonstrates how to change the default log filtering for the `My.Application.Log` object, to control what information is passed from the `Log` object to the listeners and what information is written by the listeners.</span></span> <span data-ttu-id="7f36a-104">Vous pouvez modifier le comportement de journalisation même après avoir généré l’application, car les informations de configuration sont stockées dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="7f36a-104">You can change the logging behavior even after building the application, because the configuration information is stored in the application's configuration file.</span></span>

## <a name="getting-started"></a><span data-ttu-id="7f36a-105">Mise en route</span><span class="sxs-lookup"><span data-stu-id="7f36a-105">Getting Started</span></span>

<span data-ttu-id="7f36a-106">Chaque message écrit par `My.Application.Log` a un niveau de gravité associé que les mécanismes de filtrage utilisent pour contrôler la sortie de journal.</span><span class="sxs-lookup"><span data-stu-id="7f36a-106">Each message that `My.Application.Log` writes has an associated severity level, which filtering mechanisms use to control the log output.</span></span> <span data-ttu-id="7f36a-107">Cet exemple d’application utilise les méthodes `My.Application.Log` pour écrire plusieurs messages de journal avec différents niveaux de gravité.</span><span class="sxs-lookup"><span data-stu-id="7f36a-107">This sample application uses `My.Application.Log` methods to write several log messages with different severity levels.</span></span>

#### <a name="to-build-the-sample-application"></a><span data-ttu-id="7f36a-108">Pour générer l’exemple d’application</span><span class="sxs-lookup"><span data-stu-id="7f36a-108">To build the sample application</span></span>

1. <span data-ttu-id="7f36a-109">Ouvrez un nouveau projet d’application Windows Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7f36a-109">Open a new Visual Basic Windows Application project.</span></span>

2. <span data-ttu-id="7f36a-110">Ajoutez un bouton nommé Button1 à Form1.</span><span class="sxs-lookup"><span data-stu-id="7f36a-110">Add a button named Button1 to Form1.</span></span>

3. <span data-ttu-id="7f36a-111">Dans le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> de Button1, ajoutez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="7f36a-111">In the <xref:System.Windows.Forms.Control.Click> event handler for Button1, add the following code:</span></span>

     [!code-vb[VbVbcnMyApplicationLogFiltering#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyApplicationLogFiltering/VB/Form1.vb#1)]

4. <span data-ttu-id="7f36a-112">Exécutez l’application dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="7f36a-112">Run the application in the debugger.</span></span>

5. <span data-ttu-id="7f36a-113">Appuyez sur **Button1**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-113">Press **Button1**.</span></span>

     <span data-ttu-id="7f36a-114">L’application écrit les informations suivantes dans le fichier journal et la sortie de débogage de l’application.</span><span class="sxs-lookup"><span data-stu-id="7f36a-114">The application writes the following information to the application's debug output and log file.</span></span>

     `DefaultSource Information: 0 : In Button1_Click`

     `DefaultSource Error: 2 : Error in the application.`

6. <span data-ttu-id="7f36a-115">Fermez l'application.</span><span class="sxs-lookup"><span data-stu-id="7f36a-115">Close the application.</span></span>

     <span data-ttu-id="7f36a-116">Pour plus d’informations sur la consultation de la fenêtre de sortie de débogage de l’application, consultez [Fenêtre Sortie](/visualstudio/ide/reference/output-window).</span><span class="sxs-lookup"><span data-stu-id="7f36a-116">For information on how to view the application's debug output window, see [Output Window](/visualstudio/ide/reference/output-window).</span></span> <span data-ttu-id="7f36a-117">Pour plus d’informations sur l’emplacement du fichier journal de l’application, consultez [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="7f36a-117">For information on the location of the application's log file, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="7f36a-118">Par défaut, l’application vide la sortie du fichier journal quand elle se ferme.</span><span class="sxs-lookup"><span data-stu-id="7f36a-118">By default, the application flushes the log-file output when the application closes.</span></span>

     <span data-ttu-id="7f36a-119">Dans l’exemple ci-dessus, le deuxième appel à la méthode <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> et l’appel à la méthode <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> génèrent la sortie de journal, ce qui n’est pas le cas des premier et dernier appels à la méthode `WriteEntry`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-119">In the example above, the second call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A> method and the call to the <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A> method produces log output, while the first and last calls to the `WriteEntry` method do not.</span></span> <span data-ttu-id="7f36a-120">Étant donné que les niveaux de gravité de `WriteEntry` et `WriteException` sont « Information » et « Erreur », ceux-ci sont autorisés par le filtrage de journal par défaut de l’objet `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-120">This is because the severity levels of `WriteEntry` and `WriteException` are "Information" and "Error", both of which are allowed by the `My.Application.Log` object's default log filtering.</span></span> <span data-ttu-id="7f36a-121">Toutefois, les événements avec les niveaux de gravité « Démarrage » et « Arrêt » ne peuvent pas générer une sortie de journal.</span><span class="sxs-lookup"><span data-stu-id="7f36a-121">However, events with "Start" and "Stop" severity levels are prevented from producing log output.</span></span>

## <a name="filtering-for-all-myapplicationlog-listeners"></a><span data-ttu-id="7f36a-122">Filtrage de tous les écouteurs My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="7f36a-122">Filtering for All My.Application.Log Listeners</span></span>

<span data-ttu-id="7f36a-123">L’objet `My.Application.Log` utilise un <xref:System.Diagnostics.SourceSwitch> nommé `DefaultSwitch` pour gérer les messages qu’il passe des méthodes `WriteEntry` et `WriteException` aux écouteurs de journalisation.</span><span class="sxs-lookup"><span data-stu-id="7f36a-123">The `My.Application.Log` object uses a <xref:System.Diagnostics.SourceSwitch> named `DefaultSwitch` to control which messages it passes from the `WriteEntry` and `WriteException` methods to the log listeners.</span></span> <span data-ttu-id="7f36a-124">Vous pouvez configurer `DefaultSwitch` dans le fichier de configuration de l’application en lui affectant l’une des valeurs d’énumération <xref:System.Diagnostics.SourceLevels>.</span><span class="sxs-lookup"><span data-stu-id="7f36a-124">You can configure `DefaultSwitch` in the application's configuration file by setting its value to one of the <xref:System.Diagnostics.SourceLevels> enumeration values.</span></span> <span data-ttu-id="7f36a-125">Par défaut, sa valeur est « Information ».</span><span class="sxs-lookup"><span data-stu-id="7f36a-125">By default, its value is "Information".</span></span>

<span data-ttu-id="7f36a-126">Ce tableau affiche le niveau de gravité requis pour le journal afin d’écrire un message pour les écouteurs, avec un paramètre `DefaultSwitch` particulier.</span><span class="sxs-lookup"><span data-stu-id="7f36a-126">This table shows the severity level required for Log to write a message to the listeners, given a particular `DefaultSwitch` setting.</span></span>

|<span data-ttu-id="7f36a-127">Valeur DefaultSwitch</span><span class="sxs-lookup"><span data-stu-id="7f36a-127">DefaultSwitch Value</span></span>|<span data-ttu-id="7f36a-128">Gravité du message nécessaire pour la sortie</span><span class="sxs-lookup"><span data-stu-id="7f36a-128">Message severity required for output</span></span>|
|---|---|
|`Critical`|`Critical`|
|`Error`|<span data-ttu-id="7f36a-129">`Critical` ou `Error`</span><span class="sxs-lookup"><span data-stu-id="7f36a-129">`Critical` or `Error`</span></span>|
|`Warning`|<span data-ttu-id="7f36a-130">`Critical`, `Error` ou `Warning`</span><span class="sxs-lookup"><span data-stu-id="7f36a-130">`Critical`, `Error`, or `Warning`</span></span>|
|`Information`|<span data-ttu-id="7f36a-131">`Critical`, `Error`, `Warning` ou `Information`</span><span class="sxs-lookup"><span data-stu-id="7f36a-131">`Critical`, `Error`, `Warning`, or `Information`</span></span>|
|`Verbose`|<span data-ttu-id="7f36a-132">`Critical`, `Error`, `Warning`, `Information` ou`Verbose`</span><span class="sxs-lookup"><span data-stu-id="7f36a-132">`Critical`, `Error`, `Warning`, `Information`, or `Verbose`</span></span>|
|`ActivityTracing`|<span data-ttu-id="7f36a-133">`Start`, `Stop`, `Suspend`, `Resume` ou`Transfer`</span><span class="sxs-lookup"><span data-stu-id="7f36a-133">`Start`, `Stop`, `Suspend`, `Resume`, or `Transfer`</span></span>|
|`All`|<span data-ttu-id="7f36a-134">Tous les messages sont autorisés.</span><span class="sxs-lookup"><span data-stu-id="7f36a-134">All messages are allowed.</span></span>|
|`Off`|<span data-ttu-id="7f36a-135">Tous les messages sont bloqués.</span><span class="sxs-lookup"><span data-stu-id="7f36a-135">All messages are blocked.</span></span>|

> [!NOTE]
> <span data-ttu-id="7f36a-136">Les méthodes `WriteEntry` et `WriteException` ont chacune une surcharge qui ne spécifie pas de niveau de gravité.</span><span class="sxs-lookup"><span data-stu-id="7f36a-136">The `WriteEntry` and `WriteException` methods each have an overload that does not specify a severity level.</span></span> <span data-ttu-id="7f36a-137">Le niveau de gravité implicite de la surcharge `WriteEntry` est « Information » et le niveau de gravité implicite de la surcharge `WriteException` est « Erreur ».</span><span class="sxs-lookup"><span data-stu-id="7f36a-137">The implicit severity level for the `WriteEntry` overload is "Information", and the implicit severity level for the `WriteException` overload is "Error".</span></span>

<span data-ttu-id="7f36a-138">Ce tableau explique la sortie de journal affichée dans l’exemple précédent : avec la valeur « Information » du paramètre `DefaultSwitch` par défaut, seuls le deuxième appel à la méthode `WriteEntry` et l’appel à la méthode `WriteException` génèrent la sortie de journal.</span><span class="sxs-lookup"><span data-stu-id="7f36a-138">This table explains the log output shown in the previous example: with the default `DefaultSwitch` setting of "Information", only the second call to the `WriteEntry` method and the call to the `WriteException` method produce log output.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="7f36a-139">Pour enregistrer uniquement les événements de traçage d’activités</span><span class="sxs-lookup"><span data-stu-id="7f36a-139">To log only activity tracing events</span></span>

1. <span data-ttu-id="7f36a-140">Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions** et sélectionnez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-140">Right-click app.config in the **Solution Explorer** and select **Open**.</span></span>

     <span data-ttu-id="7f36a-141">-ou-</span><span class="sxs-lookup"><span data-stu-id="7f36a-141">-or-</span></span>

     <span data-ttu-id="7f36a-142">S’il n’existe pas de fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="7f36a-142">If there is no app.config file:</span></span>

    1. <span data-ttu-id="7f36a-143">Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-143">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="7f36a-144">Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-144">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="7f36a-145">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-145">Click **Add**.</span></span>

2. <span data-ttu-id="7f36a-146">Recherchez la section `<switches>` dans la section `<system.diagnostics>`, qui se trouve dans la section `<configuration>` de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="7f36a-146">Locate the `<switches>` section, which is in the `<system.diagnostics>` section, which is in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="7f36a-147">Recherchez l’élément qui ajoute `DefaultSwitch` à la collection de commutateurs.</span><span class="sxs-lookup"><span data-stu-id="7f36a-147">Find the element that adds `DefaultSwitch` to the collection of switches.</span></span> <span data-ttu-id="7f36a-148">Il doit ressembler à l’élément ci-après :</span><span class="sxs-lookup"><span data-stu-id="7f36a-148">It should look similar to this element:</span></span>

     `<add name="DefaultSwitch" value="Information" />`

4. <span data-ttu-id="7f36a-149">Remplacez la valeur de l’attribut `value` par « ActivityTracing ».</span><span class="sxs-lookup"><span data-stu-id="7f36a-149">Change the value of the `value` attribute to "ActivityTracing".</span></span>

5. <span data-ttu-id="7f36a-150">Le contenu du fichier app.config doit être similaire au code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="7f36a-150">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="ActivityTracing" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

6. <span data-ttu-id="7f36a-151">Exécutez l’application dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="7f36a-151">Run the application in the debugger.</span></span>

7. <span data-ttu-id="7f36a-152">Appuyez sur **Button1**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-152">Press **Button1**.</span></span>

     <span data-ttu-id="7f36a-153">L’application écrit les informations suivantes dans le fichier journal et la sortie de débogage de l’application :</span><span class="sxs-lookup"><span data-stu-id="7f36a-153">The application writes the following information to the application's debug output and log file:</span></span>

     `DefaultSource Start: 4 : Entering Button1_Click`

     `DefaultSource Stop: 5 : Leaving Button1_Click`

8. <span data-ttu-id="7f36a-154">Fermez l'application.</span><span class="sxs-lookup"><span data-stu-id="7f36a-154">Close the application.</span></span>

9. <span data-ttu-id="7f36a-155">Rétablissez la valeur « Information » de l’attribut `value`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-155">Change the value of the `value` attribute back to "Information".</span></span>

    > [!NOTE]
    > <span data-ttu-id="7f36a-156">Le paramètre de commutateur `DefaultSwitch` contrôle uniquement `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-156">The `DefaultSwitch` switch setting controls only `My.Application.Log`.</span></span> <span data-ttu-id="7f36a-157">Il ne modifie pas le comportement des classes <xref:System.Diagnostics.Trace?displayProperty=nameWithType> et <xref:System.Diagnostics.Debug?displayProperty=nameWithType> .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7f36a-157">It does not change how the .NET Framework <xref:System.Diagnostics.Trace?displayProperty=nameWithType> and <xref:System.Diagnostics.Debug?displayProperty=nameWithType> classes behave.</span></span>

## <a name="individual-filtering-for-myapplicationlog-listeners"></a><span data-ttu-id="7f36a-158">Filtrage individuel des écouteurs My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="7f36a-158">Individual Filtering For My.Application.Log Listeners</span></span>

<span data-ttu-id="7f36a-159">L’exemple précédent indique comment modifier le filtrage de toute la sortie `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-159">The previous example shows how to change the filtering for all `My.Application.Log` output.</span></span> <span data-ttu-id="7f36a-160">Cet exemple montre comment filtrer un écouteur de journalisation.</span><span class="sxs-lookup"><span data-stu-id="7f36a-160">This example demonstrates how to filter an individual log listener.</span></span> <span data-ttu-id="7f36a-161">Par défaut, une application a deux écouteurs qui écrivent dans le fichier journal et la sortie de débogage de l’application.</span><span class="sxs-lookup"><span data-stu-id="7f36a-161">By default, an application has two listeners that write to the application's debug output and the log file.</span></span>

<span data-ttu-id="7f36a-162">Le fichier de configuration contrôle le comportement des écouteurs de journalisation en permettant à chacun d’eux d’avoir un filtre similaire à un commutateur pour `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-162">The configuration file controls the behavior of the log listeners by allowing each one to have a filter, which is similar to a switch for `My.Application.Log`.</span></span> <span data-ttu-id="7f36a-163">Un écouteur de journalisation ne génère un message que si la gravité de ce dernier est acceptée par le `DefaultSwitch` du journal et le filtre de l’écouteur de journalisation.</span><span class="sxs-lookup"><span data-stu-id="7f36a-163">A log listener will output a message only if the message's severity is allowed by both the log's `DefaultSwitch` and the log listener's filter.</span></span>

<span data-ttu-id="7f36a-164">Cet exemple montre comment configurer le filtrage d’un nouvel écouteur de débogage et l’ajouter à l’objet `Log`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-164">This example demonstrates how to configure filtering for a new debug listener and add it to the `Log` object.</span></span> <span data-ttu-id="7f36a-165">L’écouteur de débogage par défaut doit être supprimé de l’objet `Log` ; ainsi, il apparaît clairement que les messages de débogage proviennent du nouvel écouteur de débogage.</span><span class="sxs-lookup"><span data-stu-id="7f36a-165">The default debug listener should be removed from the `Log` object, so it is clear that the debug messages come from the new debug listener.</span></span>

#### <a name="to-log-only-activity-tracing-events"></a><span data-ttu-id="7f36a-166">Pour enregistrer uniquement les événements de traçage d’activités</span><span class="sxs-lookup"><span data-stu-id="7f36a-166">To log only activity-tracing events</span></span>

1. <span data-ttu-id="7f36a-167">Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions** et sélectionnez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-167">Right-click app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="7f36a-168">\- ou -</span><span class="sxs-lookup"><span data-stu-id="7f36a-168">\-or-</span></span>

     <span data-ttu-id="7f36a-169">S’il n’existe pas de fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="7f36a-169">If there is no app.config file:</span></span>

    1. <span data-ttu-id="7f36a-170">Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-170">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="7f36a-171">Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-171">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="7f36a-172">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-172">Click **Add**.</span></span>

2. <span data-ttu-id="7f36a-173">Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-173">Right-click app.config in **Solution Explorer**.</span></span> <span data-ttu-id="7f36a-174">Choisissez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-174">Choose **Open**.</span></span>

3. <span data-ttu-id="7f36a-175">Recherchez la section `<listeners>`, dans la section `<source>` avec l’attribut `name` « DefaultSource » sous la section `<sources>`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-175">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", which is under the `<sources>` section.</span></span> <span data-ttu-id="7f36a-176">La section `<sources>` est sous la section `<system.diagnostics>`, dans la section `<configuration>` de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="7f36a-176">The `<sources>` section is under the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

4. <span data-ttu-id="7f36a-177">Ajoutez cet élément à la section `<listeners>` :</span><span class="sxs-lookup"><span data-stu-id="7f36a-177">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <!-- Remove the default debug listener. -->
    <remove name="Default"/>
    <!-- Add a filterable debug listener. -->
    <add name="NewDefault"/>
    ```

5. <span data-ttu-id="7f36a-178">Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="7f36a-178">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="7f36a-179">Ajoutez cet élément à cette section `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="7f36a-179">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="NewDefault"
         type="System.Diagnostics.DefaultTraceListener,
               System, Version=2.0.0.0, Culture=neutral,
               PublicKeyToken=b77a5c561934e089,
               processorArchitecture=MSIL">
        <filter type="System.Diagnostics.EventTypeFilter"
                initializeData="Error" />
    </add>
    ```

     <span data-ttu-id="7f36a-180">Le filtre <xref:System.Diagnostics.EventTypeFilter> considère l’une des valeurs d’énumération <xref:System.Diagnostics.SourceLevels> comme son attribut `initializeData`.</span><span class="sxs-lookup"><span data-stu-id="7f36a-180">The <xref:System.Diagnostics.EventTypeFilter> filter takes one of the <xref:System.Diagnostics.SourceLevels> enumeration values as its `initializeData` attribute.</span></span>

7. <span data-ttu-id="7f36a-181">Le contenu du fichier app.config doit être similaire au code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="7f36a-181">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Remove the default debug listener. -->
              <remove name="Default"/>
              <!-- Add a filterable debug listener. -->
              <add name="NewDefault"/>
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a,
                     processorArchitecture=MSIL"
               initializeData="FileLogWriter"/>
          <add name="NewDefault"
               type="System.Diagnostics.DefaultTraceListener,
                     System, Version=2.0.0.0, Culture=neutral,
                     PublicKeyToken=b77a5c561934e089,
                     processorArchitecture=MSIL">
            <filter type="System.Diagnostics.EventTypeFilter"
                    initializeData="Error" />
          </add>
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

8. <span data-ttu-id="7f36a-182">Exécutez l’application dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="7f36a-182">Run the application in the debugger.</span></span>

9. <span data-ttu-id="7f36a-183">Appuyez sur **Button1**.</span><span class="sxs-lookup"><span data-stu-id="7f36a-183">Press **Button1**.</span></span>

     <span data-ttu-id="7f36a-184">L’application écrit les informations suivantes dans le fichier journal de l’application :</span><span class="sxs-lookup"><span data-stu-id="7f36a-184">The application writes the following information to the application's log file:</span></span>

     `Default Information: 0 : In Button1_Click`

     `Default Error: 2 : Error in the application.`

     <span data-ttu-id="7f36a-185">L’application écrit moins d’informations dans la sortie de débogage de l’application à cause du filtrage plus restrictif.</span><span class="sxs-lookup"><span data-stu-id="7f36a-185">The application writes less information to the application's debug output because of the more restrictive filtering.</span></span>

     `Default Error   2   Error`

10. <span data-ttu-id="7f36a-186">Fermez l'application.</span><span class="sxs-lookup"><span data-stu-id="7f36a-186">Close the application.</span></span>

<span data-ttu-id="7f36a-187">Pour plus d’informations sur la modification des paramètres de journal après le déploiement, consultez [Utilisation des journaux des applications](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="7f36a-187">For more information about changing log settings after deployment, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f36a-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f36a-188">See also</span></span>

- [<span data-ttu-id="7f36a-189">Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="7f36a-189">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
- [<span data-ttu-id="7f36a-190">Procédure pas à pas : modification de l'emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="7f36a-190">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
- [<span data-ttu-id="7f36a-191">Procédure pas à pas : création d'écouteurs de journalisation personnalisés</span><span class="sxs-lookup"><span data-stu-id="7f36a-191">Walkthrough: Creating Custom Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-creating-custom-log-listeners.md)
- [<span data-ttu-id="7f36a-192">Guide pratique : écrire des messages de journal</span><span class="sxs-lookup"><span data-stu-id="7f36a-192">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="7f36a-193">Commutateurs de traçage</span><span class="sxs-lookup"><span data-stu-id="7f36a-193">Trace Switches</span></span>](../../../../framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="7f36a-194">Enregistrement d'informations provenant de l'application</span><span class="sxs-lookup"><span data-stu-id="7f36a-194">Logging Information from the Application</span></span>](../../../../visual-basic/developing-apps/programming/log-info/index.md)
