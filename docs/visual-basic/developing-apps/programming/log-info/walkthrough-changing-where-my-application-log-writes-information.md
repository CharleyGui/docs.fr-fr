---
title: modification de l’emplacement des informations My.Application.Log
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: f9e45cdf4507840f62e32678f4c0a7be2c0be054
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398290"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="f21bf-102">Procédure pas à pas : modification de l'emplacement des informations My.Application.Log (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f21bf-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="f21bf-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="f21bf-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="f21bf-104">Cette procédure pas à pas montre comment remplacer les paramètres par défaut et faire en sorte que l’objet `Log` écrive dans d’autres écouteurs de journalisation.</span><span class="sxs-lookup"><span data-stu-id="f21bf-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f21bf-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="f21bf-105">Prerequisites</span></span>

<span data-ttu-id="f21bf-106">L’objet `Log` peut écrire des informations dans plusieurs écouteurs de journalisation.</span><span class="sxs-lookup"><span data-stu-id="f21bf-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="f21bf-107">Vous devez déterminer la configuration actuelle des écouteurs de journalisation avant de modifier les configurations.</span><span class="sxs-lookup"><span data-stu-id="f21bf-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="f21bf-108">Pour plus d’informations, consultez [Procédure pas à pas : détermination de l’emplacement des informations My.Application.Log](walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="f21bf-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

<span data-ttu-id="f21bf-109">Vous pouvez passer en revue [Guide pratique pour écrire des informations sur les événements dans un fichier texte](how-to-write-event-information-to-a-text-file.md) ou [Guide pratique pour écrire dans le journal des événements d’une application](how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="f21bf-109">You may want to review [How to: Write Event Information to a Text File](how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](how-to-write-to-an-application-event-log.md).</span></span>

### <a name="to-add-listeners"></a><span data-ttu-id="f21bf-110">Pour ajouter des écouteurs</span><span class="sxs-lookup"><span data-stu-id="f21bf-110">To add listeners</span></span>

1. <span data-ttu-id="f21bf-111">Cliquez avec le bouton droit sur app.config dans l’ **Explorateur de solutions** et choisissez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="f21bf-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="f21bf-112">\- ou -</span><span class="sxs-lookup"><span data-stu-id="f21bf-112">\- or -</span></span>

     <span data-ttu-id="f21bf-113">S’il n’existe pas de fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="f21bf-113">If there is no app.config file:</span></span>

    1. <span data-ttu-id="f21bf-114">Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="f21bf-114">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="f21bf-115">Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **Fichier de configuration de l’application**.</span><span class="sxs-lookup"><span data-stu-id="f21bf-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>

    3. <span data-ttu-id="f21bf-116">Cliquez sur **Add**.</span><span class="sxs-lookup"><span data-stu-id="f21bf-116">Click **Add**.</span></span>

2. <span data-ttu-id="f21bf-117">Recherchez la section `<listeners>` , sous la section `<source>` avec l’attribut `name` « DefaultSource » dans la section `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="f21bf-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="f21bf-118">La section `<sources>` se trouve dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="f21bf-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="f21bf-119">Ajoutez ces éléments à cette section `<listeners>` .</span><span class="sxs-lookup"><span data-stu-id="f21bf-119">Add these elements to that `<listeners>` section.</span></span>

    ```xml
    <!-- Uncomment to connect the application file log. -->
    <!-- <add name="FileLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="EventLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="Delimited" /> -->
    <!-- Uncomment to connect the XML log. -->
    <!-- <add name="XmlWriter" /> -->
    <!-- Uncomment to connect the console log. -->
    <!-- <add name="Console" /> -->
    ```

4. <span data-ttu-id="f21bf-120">Supprimez les marques de commentaire pour les écouteurs de journalisation qui doivent recevoir les messages `Log` .</span><span class="sxs-lookup"><span data-stu-id="f21bf-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>

5. <span data-ttu-id="f21bf-121">Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="f21bf-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="f21bf-122">Ajoutez ces éléments à cette section `<sharedListeners>` .</span><span class="sxs-lookup"><span data-stu-id="f21bf-122">Add these elements to that `<sharedListeners>` section.</span></span>

    ```xml
    <add name="FileLog"
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
               Microsoft.VisualBasic, Version=8.0.0.0,
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
         initializeData="FileLogWriter" />
    <add name="EventLog"
         type="System.Diagnostics.EventLogTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="sample application"/>
    <add name="Delimited"
         type="System.Diagnostics.DelimitedListTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleDelimitedFile.txt"
         traceOutputOptions="DateTime" />
    <add name="XmlWriter"
         type="System.Diagnostics.XmlWriterTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleLogFile.xml" />
    <add name="Console"
         type="System.Diagnostics.ConsoleTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="true" />
    ```

7. <span data-ttu-id="f21bf-123">Le contenu du fichier app.config doit être similaire au code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="f21bf-123">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Uncomment to connect the application file log. -->
              <!-- <add name="FileLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="EventLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="Delimited" /> -->
              <!-- Uncomment to connect the XML log. -->
              <!-- <add name="XmlWriter" /> -->
              <!-- Uncomment to connect the console log. -->
              <!-- <add name="Console" /> -->
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
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
               initializeData="FileLogWriter" />
          <add name="EventLog"
               type="System.Diagnostics.EventLogTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="sample application"/>
          <add name="Delimited"
               type="System.Diagnostics.DelimitedListTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleDelimitedFile.txt"
               traceOutputOptions="DateTime" />
          <add name="XmlWriter"
               type="System.Diagnostics.XmlWriterTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleLogFile.xml" />
          <add name="Console"
               type="System.Diagnostics.ConsoleTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="true" />
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="f21bf-124">Pour reconfigurer un écouteur</span><span class="sxs-lookup"><span data-stu-id="f21bf-124">To reconfigure a listener</span></span>

1. <span data-ttu-id="f21bf-125">Recherchez l’élément `<add>` de l’écouteur dans la section `<sharedListeners>` .</span><span class="sxs-lookup"><span data-stu-id="f21bf-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>

2. <span data-ttu-id="f21bf-126">L’attribut `type` donne le nom du type d’écouteur.</span><span class="sxs-lookup"><span data-stu-id="f21bf-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="f21bf-127">Ce type doit être hérité de la classe <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="f21bf-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="f21bf-128">Utilisez le nom de type avec un nom fort pour être sûr que le type correct est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f21bf-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="f21bf-129">Pour plus d’informations, consultez la section « Pour référencer un type avec un nom fort » ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="f21bf-129">For more information, see the "To reference a strongly named type" section below.</span></span>

     <span data-ttu-id="f21bf-130">Voici quelques-uns des types que vous pouvez utiliser :</span><span class="sxs-lookup"><span data-stu-id="f21bf-130">Some types that you can use are:</span></span>

    - <span data-ttu-id="f21bf-131">Un écouteur <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> , qui écrit dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="f21bf-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>

    - <span data-ttu-id="f21bf-132">Un écouteur <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> , qui écrit les informations dans le journal des événements de l’ordinateur spécifié par le paramètre `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="f21bf-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>

    - <span data-ttu-id="f21bf-133">Les écouteurs <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> et <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> , qui écrivent dans le fichier spécifié par le paramètre `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="f21bf-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="f21bf-134">Un écouteur <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> , qui écrit dans la console de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="f21bf-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>

     <span data-ttu-id="f21bf-135">Pour plus d’informations sur les emplacements où d’autres types d’écouteurs de journalisation écrivent les informations, consultez la documentation de ce type.</span><span class="sxs-lookup"><span data-stu-id="f21bf-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

3. <span data-ttu-id="f21bf-136">Quand l’application crée l’objet d’écouteur de journalisation, il passe l’attribut `initializeData` comme paramètre de constructeur.</span><span class="sxs-lookup"><span data-stu-id="f21bf-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="f21bf-137">La signification de l’attribut `initializeData` dépend de l’écouteur de suivi.</span><span class="sxs-lookup"><span data-stu-id="f21bf-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>

4. <span data-ttu-id="f21bf-138">Après avoir créé l’écouteur de journalisation, l’application définit les propriétés de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="f21bf-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="f21bf-139">Ces propriétés sont définies par les autres attributs dans l’élément `<add>` .</span><span class="sxs-lookup"><span data-stu-id="f21bf-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="f21bf-140">Pour plus d’informations sur les propriétés d’un écouteur particulier, consultez la documentation de ce type d’écouteur.</span><span class="sxs-lookup"><span data-stu-id="f21bf-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>

### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="f21bf-141">Pour référencer un type avec un nom fort</span><span class="sxs-lookup"><span data-stu-id="f21bf-141">To reference a strongly named type</span></span>

1. <span data-ttu-id="f21bf-142">Pour être sûr que type correct est utilisé pour votre écouteur de journalisation, vérifiez que vous utilisez le nom de type qualifié complet et le nom d’assembly avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="f21bf-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="f21bf-143">La syntaxe d’un type avec nom fort est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f21bf-143">The syntax of a strongly named type is as follows:</span></span>

     <span data-ttu-id="f21bf-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span><span class="sxs-lookup"><span data-stu-id="f21bf-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>

2. <span data-ttu-id="f21bf-145">Cet exemple de code montre comment déterminer le nom de type avec nom fort pour un type qualifié complet, dans ce cas « System.Diagnostics.FileLogTraceListener ».</span><span class="sxs-lookup"><span data-stu-id="f21bf-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     <span data-ttu-id="f21bf-146">Voici la sortie. Il peut être utilisé pour faire référence de façon univoque à un type avec nom fort, comme dans la procédure « Pour ajouter des écouteurs » ci-dessus.</span><span class="sxs-lookup"><span data-stu-id="f21bf-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a><span data-ttu-id="f21bf-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f21bf-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="f21bf-148">Procédure : écrire des informations sur les événements dans un fichier texte</span><span class="sxs-lookup"><span data-stu-id="f21bf-148">How to: Write Event Information to a Text File</span></span>](how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="f21bf-149">Procédure : écrire dans le journal des événements de l’application</span><span class="sxs-lookup"><span data-stu-id="f21bf-149">How to: Write to an Application Event Log</span></span>](how-to-write-to-an-application-event-log.md)
