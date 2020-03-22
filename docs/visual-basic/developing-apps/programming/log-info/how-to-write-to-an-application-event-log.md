---
title: "Comment : écrire dans le journal des événements de l'application"
ms.date: 07/20/2015
helpviewer_keywords:
- Computer.EventLog element
- WriteEntry method [Visual Basic]
- My.Computer.EventLog element
- event logs, writing to
ms.assetid: cadbc8c1-87af-4746-934e-55b79a4f6e2b
ms.openlocfilehash: 511bb8fb16851872c1a16ae7627ed0fc6594337c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352045"
---
# <a name="how-to-write-to-an-application-event-log-visual-basic"></a><span data-ttu-id="78f7c-102">Comment : écrire dans le journal des événements de l'application (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="78f7c-102">How to: Write to an Application Event Log (Visual Basic)</span></span>

<span data-ttu-id="78f7c-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour écrire des informations sur les événements qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="78f7c-103">You can use the `My.Application.Log` and `My.Log` objects to write information about events that occur in your application.</span></span> <span data-ttu-id="78f7c-104">Cet exemple montre comment configurer un écouteur de journalisation des événements pour que `My.Application.Log` écrive les informations de suivi dans le journal des événements de l’application.</span><span class="sxs-lookup"><span data-stu-id="78f7c-104">This example shows how to configure an event log listener so `My.Application.Log` writes tracing information to the Application event log.</span></span>

<span data-ttu-id="78f7c-105">Vous ne pouvez pas écrire dans le journal de sécurité.</span><span class="sxs-lookup"><span data-stu-id="78f7c-105">You cannot write to the Security log.</span></span> <span data-ttu-id="78f7c-106">Pour pouvoir écrire dans le journal système, vous devez être membre du compte LocalSystem ou Administrateur.</span><span class="sxs-lookup"><span data-stu-id="78f7c-106">In order to write to the System log, you must be a member of the LocalSystem or Administrator account.</span></span>

<span data-ttu-id="78f7c-107">Pour afficher un journal des événements, vous pouvez utiliser l’ **Explorateur de serveurs** ou l’ **Observateur d’événements Windows**.</span><span class="sxs-lookup"><span data-stu-id="78f7c-107">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="78f7c-108">Pour plus d’informations, consultez [Événements ETW dans le .NET Framework](../../../../framework/performance/etw-events.md).</span><span class="sxs-lookup"><span data-stu-id="78f7c-108">For more information, see [ETW Events in the .NET Framework](../../../../framework/performance/etw-events.md).</span></span>

## <a name="to-add-and-configure-the-event-log-listener"></a><span data-ttu-id="78f7c-109">Pour ajouter et configurer l’écouteur de journalisation des événements</span><span class="sxs-lookup"><span data-stu-id="78f7c-109">To add and configure the event log listener</span></span>

1. <span data-ttu-id="78f7c-110">Cliquez avec le bouton droit sur app.config dans l’ **Explorateur de solutions** et choisissez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="78f7c-110">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

    <span data-ttu-id="78f7c-111">\- ou -</span><span class="sxs-lookup"><span data-stu-id="78f7c-111">\- or -</span></span>

    <span data-ttu-id="78f7c-112">S’il n’existe pas de fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="78f7c-112">If there is no app.config file,</span></span>

    1. <span data-ttu-id="78f7c-113">Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="78f7c-113">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="78f7c-114">Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.</span><span class="sxs-lookup"><span data-stu-id="78f7c-114">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="78f7c-115">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="78f7c-115">Click **Add**.</span></span>

2. <span data-ttu-id="78f7c-116">Recherchez la section `<listeners>` dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="78f7c-116">Locate the `<listeners>` section in the application configuration file.</span></span>

    <span data-ttu-id="78f7c-117">Vous pouvez trouver la section `<listeners>` dans la section `<source>` avec l’attribut de nom « DefaultSource », qui est imbriquée dans la section `<system.diagnostics>` , elle-même imbriquée sous la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="78f7c-117">You will find the `<listeners>` section in the `<source>` section with the name attribute "DefaultSource", which is nested under the `<system.diagnostics>` section, which is nested under the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="78f7c-118">Ajoutez cet élément à cette section `<listeners>` :</span><span class="sxs-lookup"><span data-stu-id="78f7c-118">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="EventLog"/>
    ```

4. <span data-ttu-id="78f7c-119">Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="78f7c-119">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="78f7c-120">Ajoutez cet élément à cette section `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="78f7c-120">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="EventLog"
        type="System.Diagnostics.EventLogTraceListener, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="APPLICATION_NAME"/>
    ```

    <span data-ttu-id="78f7c-121">Remplacez `APPLICATION_NAME` par le nom de votre application.</span><span class="sxs-lookup"><span data-stu-id="78f7c-121">Replace `APPLICATION_NAME` with the name of your application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="78f7c-122">En règle générale, une application écrit les erreurs seulement dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="78f7c-122">Typically, an application writes only errors to the event log.</span></span> <span data-ttu-id="78f7c-123">Pour plus d’informations sur le filtrage de la sortie du journal, consultez [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span><span class="sxs-lookup"><span data-stu-id="78f7c-123">For information on filtering log output, see [Walkthrough: Filtering My.Application.Log Output](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-filtering-my-application-log-output.md).</span></span>

## <a name="to-write-event-information-to-the-event-log"></a><span data-ttu-id="78f7c-124">Pour écrire des informations sur les événements dans le journal des événements</span><span class="sxs-lookup"><span data-stu-id="78f7c-124">To write event information to the event log</span></span>

<span data-ttu-id="78f7c-125">Utilisez la méthode `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` pour écrire des informations dans le journal des événements.</span><span class="sxs-lookup"><span data-stu-id="78f7c-125">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the event log.</span></span> <span data-ttu-id="78f7c-126">Pour plus d’informations, consultez [Guide pratique pour écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) et [Guide pratique pour enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="78f7c-126">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="78f7c-127">Une fois l’écouteur de journalisation des événements configuré pour un assembly, il reçoit tous les messages écrits par `My.Application.Log` depuis cet assembly.</span><span class="sxs-lookup"><span data-stu-id="78f7c-127">After you configure the event log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="78f7c-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="78f7c-128">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="78f7c-129">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="78f7c-129">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="78f7c-130">Comment : enregistrer des exceptions</span><span class="sxs-lookup"><span data-stu-id="78f7c-130">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="78f7c-131">Procédure pas à pas : détermination de l'emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="78f7c-131">Walkthrough: Determining Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md)
