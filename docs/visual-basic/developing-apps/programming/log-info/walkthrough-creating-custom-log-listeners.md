---
title: création d’écouteurs de journalisation personnalisés
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 7b611e93119dc66a9404cf271ea201676d7b5318
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "74353623"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="1da41-102">Procédure pas à pas : création d'écouteurs de journalisation personnalisés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1da41-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>

<span data-ttu-id="1da41-103">Cette procédure pas à pas illustre comment créer un écouteur de journalisation personnalisé et le configurer pour écouter la sortie de l’objet `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="1da41-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>

## <a name="getting-started"></a><span data-ttu-id="1da41-104">Mise en route</span><span class="sxs-lookup"><span data-stu-id="1da41-104">Getting Started</span></span>

<span data-ttu-id="1da41-105">Les écouteurs de journalisation doivent hériter de la classe <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="1da41-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>

#### <a name="to-create-the-listener"></a><span data-ttu-id="1da41-106">Pour créer l’écouteur</span><span class="sxs-lookup"><span data-stu-id="1da41-106">To create the listener</span></span>

- <span data-ttu-id="1da41-107">Dans votre application, créez une classe nommée `SimpleListener` qui hérite de <xref:System.Diagnostics.TraceListener>.</span><span class="sxs-lookup"><span data-stu-id="1da41-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]

     <span data-ttu-id="1da41-108">Les méthodes <xref:System.Diagnostics.TraceListener.Write%2A> et <xref:System.Diagnostics.TraceListener.WriteLine%2A>, requises par la classe de base, appellent `MsgBox` pour afficher leur entrée.</span><span class="sxs-lookup"><span data-stu-id="1da41-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>

     <span data-ttu-id="1da41-109">L’attribut <xref:System.Security.Permissions.HostProtectionAttribute> est appliqué aux méthodes <xref:System.Diagnostics.TraceListener.Write%2A> et <xref:System.Diagnostics.TraceListener.WriteLine%2A> afin que leurs attributs correspondent aux méthodes de classe de base.</span><span class="sxs-lookup"><span data-stu-id="1da41-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="1da41-110">L’attribut <xref:System.Security.Permissions.HostProtectionAttribute> permet à l’hôte qui exécute le code de déterminer que ce dernier expose la synchronisation de la protection de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="1da41-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>

    > [!NOTE]
    > <span data-ttu-id="1da41-111">L’attribut <xref:System.Security.Permissions.HostProtectionAttribute> n’est effectif que sur les applications non managées, telles que SQL Server, qui hébergent le Common Language Runtime et implémentent la protection de l’hôte.</span><span class="sxs-lookup"><span data-stu-id="1da41-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>

<span data-ttu-id="1da41-112">Pour vérifier que `My.Application.Log` utilise votre écouteur de journalisation, vous devez attribuer un nom fort à l’assembly qui le contient.</span><span class="sxs-lookup"><span data-stu-id="1da41-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>

<span data-ttu-id="1da41-113">La procédure suivante fournit des étapes simples pour créer un assembly d’écouteur de journalisation portant un nom fort.</span><span class="sxs-lookup"><span data-stu-id="1da41-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="1da41-114">Pour plus d’informations, consultez [Création et utilisation d’assemblys avec nom fort](../../../../standard/assembly/create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="1da41-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../standard/assembly/create-use-strong-named.md).</span></span>

#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="1da41-115">Pour attribuer un nom fort à l’assembly de l’écouteur de journalisation</span><span class="sxs-lookup"><span data-stu-id="1da41-115">To strongly name the log-listener assembly</span></span>

1. <span data-ttu-id="1da41-116">Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="1da41-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1da41-117">Sur le menu du **projet,** choisissez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1da41-117">On the **Project** menu, choose **Properties**.</span></span>

2. <span data-ttu-id="1da41-118">Cliquez sur l'onglet **Signature** .</span><span class="sxs-lookup"><span data-stu-id="1da41-118">Click the **Signing** tab.</span></span>

3. <span data-ttu-id="1da41-119">Sélectionnez la zone **Signer l'assembly** .</span><span class="sxs-lookup"><span data-stu-id="1da41-119">Select the **Sign the assembly** box.</span></span>

4. <span data-ttu-id="1da41-120">Sélectionnez \*\* \<New>\*\* de la liste d’abandon de **fichiers clés De nom fort.**</span><span class="sxs-lookup"><span data-stu-id="1da41-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>

     <span data-ttu-id="1da41-121">La boîte de dialogue **Créer une clé de nom fort** s’ouvre.</span><span class="sxs-lookup"><span data-stu-id="1da41-121">The **Create Strong Name Key** dialog box opens.</span></span>

5. <span data-ttu-id="1da41-122">Fournissez un nom pour le fichier de clé dans la zone **Nom du fichier de clé**.</span><span class="sxs-lookup"><span data-stu-id="1da41-122">Provide a name for the key file in the **Key file name** box.</span></span>

6. <span data-ttu-id="1da41-123">Entrez un mot de passe dans les zones **Entrer le mot de passe** et **Confirmer le mot de passe**.</span><span class="sxs-lookup"><span data-stu-id="1da41-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>

7. <span data-ttu-id="1da41-124">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="1da41-124">Click **OK**.</span></span>

8. <span data-ttu-id="1da41-125">Régénérez l’application.</span><span class="sxs-lookup"><span data-stu-id="1da41-125">Rebuild the application.</span></span>

## <a name="adding-the-listener"></a><span data-ttu-id="1da41-126">Ajout de l’écouteur</span><span class="sxs-lookup"><span data-stu-id="1da41-126">Adding the Listener</span></span>

<span data-ttu-id="1da41-127">Maintenant que l’assembly a un nom fort, vous devez déterminer le nom fort de l’écouteur afin que `My.Application.Log` utilise votre écouteur de journalisation.</span><span class="sxs-lookup"><span data-stu-id="1da41-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>

<span data-ttu-id="1da41-128">Le format d’un type portant un nom fort se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="1da41-128">The format of a strongly named type is as follows.</span></span>

<span data-ttu-id="1da41-129">\<nom type>, \<nom assembly>, \<numéro version>, \<culture>, \<nom fort></span><span class="sxs-lookup"><span data-stu-id="1da41-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>

#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="1da41-130">Pour déterminer le nom fort de l’écouteur</span><span class="sxs-lookup"><span data-stu-id="1da41-130">To determine the strong name of the listener</span></span>

- <span data-ttu-id="1da41-131">Le code suivant indique comment déterminer le nom de type fort pour `SimpleListener`.</span><span class="sxs-lookup"><span data-stu-id="1da41-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]

     <span data-ttu-id="1da41-132">Le nom fort du type dépend de votre projet.</span><span class="sxs-lookup"><span data-stu-id="1da41-132">The strong name of the type depends on your project.</span></span>

<span data-ttu-id="1da41-133">Avec le nom fort, vous pouvez ajouter l’écouteur à la collection de l’écouteur de journalisation `My.Application.Log`.</span><span class="sxs-lookup"><span data-stu-id="1da41-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>

#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="1da41-134">Pour ajouter l’écouteur à My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="1da41-134">To add the listener to My.Application.Log</span></span>

1. <span data-ttu-id="1da41-135">Cliquez avec le bouton droit sur app.config dans l’**Explorateur de solutions** et sélectionnez **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="1da41-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="1da41-136">-ou-</span><span class="sxs-lookup"><span data-stu-id="1da41-136">-or-</span></span>

     <span data-ttu-id="1da41-137">S’il existe un fichier app.config :</span><span class="sxs-lookup"><span data-stu-id="1da41-137">If there is an app.config file:</span></span>

    1. <span data-ttu-id="1da41-138">Dans le menu **Projet** , choisissez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="1da41-138">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="1da41-139">Dans la boîte de dialogue **Ajouter un nouvel élément** , choisissez **Fichier de configuration de l’application**.</span><span class="sxs-lookup"><span data-stu-id="1da41-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="1da41-140">Cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="1da41-140">Click **Add**.</span></span>

2. <span data-ttu-id="1da41-141">Recherchez la section `<listeners>` dans la section `<source>` avec l’attribut `name` « DefaultSource », qui se trouve dans la section `<sources>` .</span><span class="sxs-lookup"><span data-stu-id="1da41-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="1da41-142">La section `<sources>` se trouve dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="1da41-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="1da41-143">Ajoutez cet élément à la section `<listeners>` :</span><span class="sxs-lookup"><span data-stu-id="1da41-143">Add this element to the `<listeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" />
    ```

4. <span data-ttu-id="1da41-144">Recherchez la section `<sharedListeners>` dans la section `<system.diagnostics>` , dans la section `<configuration>` de plus haut niveau.</span><span class="sxs-lookup"><span data-stu-id="1da41-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="1da41-145">Ajoutez cet élément à cette section `<sharedListeners>` :</span><span class="sxs-lookup"><span data-stu-id="1da41-145">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="SimpleLog" type="SimpleLogStrongName" />
    ```

     <span data-ttu-id="1da41-146">Modifiez la valeur de `SimpleLogStrongName` pour qu’elle soit le nom fort de l’écouteur.</span><span class="sxs-lookup"><span data-stu-id="1da41-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>

## <a name="see-also"></a><span data-ttu-id="1da41-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1da41-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="1da41-148">Utilisation des journaux des applications</span><span class="sxs-lookup"><span data-stu-id="1da41-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="1da41-149">Comment : enregistrer des exceptions</span><span class="sxs-lookup"><span data-stu-id="1da41-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="1da41-150">Guide pratique : écrire des messages de journal</span><span class="sxs-lookup"><span data-stu-id="1da41-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="1da41-151">Procédure pas à pas : modification de l'emplacement des informations My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="1da41-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
