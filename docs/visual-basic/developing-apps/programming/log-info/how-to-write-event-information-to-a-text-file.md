---
title: 'Procédure : écrire des informations sur les événements dans un fichier texte'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352073"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="bf57f-102">Guide pratique pour écrire des informations sur des événements dans un fichier texte (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf57f-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="bf57f-103">Vous pouvez utiliser les objets `My.Application.Log` et `My.Log` pour enregistrer des informations sur les événements qui se produisent dans votre application.</span><span class="sxs-lookup"><span data-stu-id="bf57f-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="bf57f-104">Cet exemple montre comment utiliser la méthode `My.Application.Log.WriteEntry` pour enregistrer des informations de traçage dans un fichier journal.</span><span class="sxs-lookup"><span data-stu-id="bf57f-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="bf57f-105">Pour ajouter et configurer l’écouteur de journalisation du fichier</span><span class="sxs-lookup"><span data-stu-id="bf57f-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="bf57f-106">Cliquez avec le bouton droit sur app.config dans l’ **Explorateur de solutions** et choisissez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="bf57f-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="bf57f-107">\- ou -</span><span class="sxs-lookup"><span data-stu-id="bf57f-107">\- or -</span></span>

     <span data-ttu-id="bf57f-108">S’il n’existe pas de fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="bf57f-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="bf57f-109">Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="bf57f-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="bf57f-110">Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.</span><span class="sxs-lookup"><span data-stu-id="bf57f-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="bf57f-111">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="bf57f-111">Click **Add**.</span></span>

2. <span data-ttu-id="bf57f-112">Recherchez la section `<listeners>` dans le fichier de configuration de l’application.</span><span class="sxs-lookup"><span data-stu-id="bf57f-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="bf57f-113">Vous pouvez trouver la section \<listeners> dans la section \<source> avec l’attribut de nom « DefaultSource », qui est imbriquée dans la section \<system.diagnostics>, elle-même imbriquée sous la section \<configuration> de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="bf57f-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="bf57f-114">Ajoutez cet élément à cette section `<listeners>` :</span><span class="sxs-lookup"><span data-stu-id="bf57f-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="bf57f-115">Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>`, imbriquée dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="bf57f-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="bf57f-116">Ajoutez cet élément à cette section `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="bf57f-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="bf57f-117">Remplacez la valeur de l’attribut `customlocation` par le répertoire du journal.</span><span class="sxs-lookup"><span data-stu-id="bf57f-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bf57f-118">Pour définir la valeur d’une propriété d’écouteur, utilisez un attribut qui a le même nom que la propriété, en utilisant des minuscules.</span><span class="sxs-lookup"><span data-stu-id="bf57f-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="bf57f-119">Par exemple, les attributs `location` et `customlocation` définissent les valeurs des propriétés <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> et <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.</span><span class="sxs-lookup"><span data-stu-id="bf57f-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="bf57f-120">Pour écrire des informations sur les événements dans le journal du fichier</span><span class="sxs-lookup"><span data-stu-id="bf57f-120">To write event information to the file log</span></span>

<span data-ttu-id="bf57f-121">Utilisez la méthode `My.Application.Log.WriteEntry` ou `My.Application.Log.WriteException` pour écrire des informations dans le journal du fichier.</span><span class="sxs-lookup"><span data-stu-id="bf57f-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="bf57f-122">Pour plus d’informations, consultez [Guide pratique pour écrire des messages de journal](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) et [Guide pratique pour enregistrer des exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="bf57f-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="bf57f-123">Une fois l’écouteur de journalisation du fichier configuré pour un assembly, il reçoit tous les messages écrits par `My.Application.Log` à partir de cet assembly.</span><span class="sxs-lookup"><span data-stu-id="bf57f-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf57f-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf57f-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="bf57f-125">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="bf57f-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="bf57f-126">Procédure : journaliser des exceptions</span><span class="sxs-lookup"><span data-stu-id="bf57f-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
