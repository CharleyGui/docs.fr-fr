---
title: 'Comment : créer, initialiser et configurer les commutateurs de traçage'
description: Créez, initialisez et configurez les commutateurs de trace à l’aide des classes System. Diagnostics. BooleanSwitch et System. Diagnostics. TraceSwitch dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
ms.openlocfilehash: 6a43e143abba96c841f04b7be9d482c55e78aa8f
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: fr-FR
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051322"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="e1d67-103">Comment : créer, initialiser et configurer les commutateurs de traçage</span><span class="sxs-lookup"><span data-stu-id="e1d67-103">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="e1d67-104">Les commutateurs de trace vous permettent d'activer ou de désactiver la sortie de traçage, et de la filtrer.</span><span class="sxs-lookup"><span data-stu-id="e1d67-104">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="e1d67-105">Création et initialisation d’un commutateur de suivi</span><span class="sxs-lookup"><span data-stu-id="e1d67-105">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="e1d67-106">Pour pouvoir utiliser des commutateurs de trace, vous devez tout d'abord les créer et les placer dans votre code.</span><span class="sxs-lookup"><span data-stu-id="e1d67-106">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="e1d67-107">Il existe deux classes prédéfinies à partir desquelles vous pouvez créer des objets commutateur : la classe <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> et la classe <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1d67-107">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="e1d67-108">Utilisez <xref:System.Diagnostics.BooleanSwitch> si vous souhaitez uniquement contrôler l'affichage des messages de trace. Utilisez <xref:System.Diagnostics.TraceSwitch> si vous avez besoin de faire la distinction entre plusieurs niveaux de trace.</span><span class="sxs-lookup"><span data-stu-id="e1d67-108">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="e1d67-109">Si vous utilisez un commutateur <xref:System.Diagnostics.TraceSwitch>, vous pouvez définir vos propres messages de débogage et les associer à différents niveaux de trace.</span><span class="sxs-lookup"><span data-stu-id="e1d67-109">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="e1d67-110">Vous pouvez utiliser les deux types de commutateurs pour le traçage ou le débogage.</span><span class="sxs-lookup"><span data-stu-id="e1d67-110">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="e1d67-111">Par défaut, <xref:System.Diagnostics.BooleanSwitch> est désactivé et <xref:System.Diagnostics.TraceSwitch> est associé au niveau <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e1d67-111">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e1d67-112">Vous pouvez placer les commutateurs de trace que vous créez dans toute partie de votre code susceptible de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="e1d67-112">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="e1d67-113">Vous avez la possibilité de définir les niveaux de trace et d'autres options de configuration directement dans le code, mais il est recommandé d'utiliser le fichier de configuration pour gérer l'état de vos commutateurs.</span><span class="sxs-lookup"><span data-stu-id="e1d67-113">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="e1d67-114">La gestion de la configuration de vos commutateurs dans le système de configuration vous donne en effet plus de souplesse : vous pouvez activer ou désactiver plusieurs commutateurs et changer de niveau sans avoir à recompiler votre application.</span><span class="sxs-lookup"><span data-stu-id="e1d67-114">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="e1d67-115">Pour créer et initialiser un commutateur de trace</span><span class="sxs-lookup"><span data-stu-id="e1d67-115">To create and initialize a trace switch</span></span>  
  
1. <span data-ttu-id="e1d67-116">Définissez un commutateur de type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> ou de type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, puis indiquez le nom et la description du commutateur.</span><span class="sxs-lookup"><span data-stu-id="e1d67-116">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2. <span data-ttu-id="e1d67-117">Configurez votre commutateur de trace.</span><span class="sxs-lookup"><span data-stu-id="e1d67-117">Configure your trace switch.</span></span> <span data-ttu-id="e1d67-118">Pour plus d’informations, consultez [Configuration des commutateurs de suivi](#configure).</span><span class="sxs-lookup"><span data-stu-id="e1d67-118">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="e1d67-119">Le code suivant crée deux commutateurs, un de chaque type :</span><span class="sxs-lookup"><span data-stu-id="e1d67-119">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =
       new System.Diagnostics.TraceSwitch("General",
       "Entire application");  
    ```  
  
<a name="configure"></a>
## <a name="configuring-trace-switches"></a><span data-ttu-id="e1d67-120">Configuration des commutateurs de suivi</span><span class="sxs-lookup"><span data-stu-id="e1d67-120">Configuring trace switches</span></span>  
 <span data-ttu-id="e1d67-121">Après avoir distribué votre application, vous gardez la possibilité d'activer ou de désactiver la sortie de trace en configurant les commutateurs de trace dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e1d67-121">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="e1d67-122">Pour configurer un commutateur, il faut modifier sa valeur à partir d'une source externe une fois qu'il a été initialisé.</span><span class="sxs-lookup"><span data-stu-id="e1d67-122">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="e1d67-123">Vous pouvez modifier les valeurs des objets commutateur à l'aide du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e1d67-123">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="e1d67-124">Vous configurez un commutateur de trace pour pouvoir l'activer et le désactiver ou pour définir le niveau de trace associé, qui détermine la quantité et le type de messages qu'il transmet aux écouteurs.</span><span class="sxs-lookup"><span data-stu-id="e1d67-124">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="e1d67-125">Vos commutateurs sont configurés à l'aide du fichier .config.</span><span class="sxs-lookup"><span data-stu-id="e1d67-125">Your switches are configured using the .config file.</span></span> <span data-ttu-id="e1d67-126">Pour une application web, il s'agit du fichier Web.config associé au projet.</span><span class="sxs-lookup"><span data-stu-id="e1d67-126">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="e1d67-127">Dans une application Windows, ce fichier est nommé (nom de l’application) .exe.config. Dans une application déployée, ce fichier doit résider dans le même dossier que l’exécutable.</span><span class="sxs-lookup"><span data-stu-id="e1d67-127">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="e1d67-128">Quand votre application exécute le code qui crée pour la première fois une instance d'un commutateur, elle recherche dans le fichier de configuration des informations sur le niveau de trace défini pour le commutateur indiqué.</span><span class="sxs-lookup"><span data-stu-id="e1d67-128">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="e1d67-129">Le système de traçage examine le fichier de configuration une seule fois pour un commutateur donné (la première fois que votre application crée le commutateur).</span><span class="sxs-lookup"><span data-stu-id="e1d67-129">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="e1d67-130">Dans une application déployée, vous activez le code de trace en reconfigurant les objets commutateur quand votre application n'est pas en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="e1d67-130">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="e1d67-131">Généralement, cela implique l'activation et la désactivation des objets commutateur ou le changement des niveaux de trace, puis le redémarrage de votre application.</span><span class="sxs-lookup"><span data-stu-id="e1d67-131">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="e1d67-132">Quand vous créez une instance d’un commutateur, vous l’initialisez également en spécifiant deux arguments : l’argument *displayName* et l’argument *description*.</span><span class="sxs-lookup"><span data-stu-id="e1d67-132">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="e1d67-133">L’argument *displayName* du constructeur définit la propriété <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> de l’instance de classe <xref:System.Diagnostics.Switch>.</span><span class="sxs-lookup"><span data-stu-id="e1d67-133">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="e1d67-134">L’argument *displayName* correspond au nom utilisé pour configurer le commutateur dans le fichier .config. L’argument *description* doit normalement retourner une brève description du commutateur, ainsi que les messages qu’il contrôle.</span><span class="sxs-lookup"><span data-stu-id="e1d67-134">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="e1d67-135">En plus de spécifier le nom du commutateur que vous configurez, vous devez lui attribuer une valeur.</span><span class="sxs-lookup"><span data-stu-id="e1d67-135">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="e1d67-136">Cette valeur est un nombre entier.</span><span class="sxs-lookup"><span data-stu-id="e1d67-136">This value is an Integer.</span></span> <span data-ttu-id="e1d67-137">Pour <xref:System.Diagnostics.BooleanSwitch>, la valeur zéro (0) correspond à **Off** (Désactivé), et toute autre valeur correspond à **On** (Activé).</span><span class="sxs-lookup"><span data-stu-id="e1d67-137">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="e1d67-138">Pour <xref:System.Diagnostics.TraceSwitch>, les valeurs 0, 1, 2, 3 et 4 correspondent respectivement à **Off** (Désactivé), **Error** (Erreur), **Warning** (Avertissement), **Info** (Information) et **Verbose** (Commentaires).</span><span class="sxs-lookup"><span data-stu-id="e1d67-138">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="e1d67-139">Toute valeur supérieure à 4 est traitée comme **Verbose**, et toute valeur inférieure à 0 est traitée comme **Off**.</span><span class="sxs-lookup"><span data-stu-id="e1d67-139">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1d67-140">Dans .NET Framework 2.0, vous pouvez spécifier la valeur d'un commutateur avec du texte.</span><span class="sxs-lookup"><span data-stu-id="e1d67-140">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="e1d67-141">Par exemple, `true` pour un commutateur <xref:System.Diagnostics.BooleanSwitch> ou le texte représentant une valeur d'énumération comme `Error` pour un commutateur <xref:System.Diagnostics.TraceSwitch>.</span><span class="sxs-lookup"><span data-stu-id="e1d67-141">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="e1d67-142">La ligne `<add name="myTraceSwitch" value="Error" />` équivaut à `<add name="myTraceSwitch" value="1" />`.</span><span class="sxs-lookup"><span data-stu-id="e1d67-142">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="e1d67-143">Pour que les utilisateurs finals puissent configurer les commutateurs de trace d'une application, vous devez fournir des informations détaillées sur les commutateurs dans votre application.</span><span class="sxs-lookup"><span data-stu-id="e1d67-143">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="e1d67-144">Décrivez en détail ce que les commutateurs contrôlent et comment ils peuvent être activés ou désactivés.</span><span class="sxs-lookup"><span data-stu-id="e1d67-144">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="e1d67-145">Transmettez également aux utilisateurs finals un fichier .config contenant l'aide nécessaire dans les commentaires.</span><span class="sxs-lookup"><span data-stu-id="e1d67-145">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="e1d67-146">Pour configurer les commutateurs de trace</span><span class="sxs-lookup"><span data-stu-id="e1d67-146">To configure trace switches</span></span>  
  
1. <span data-ttu-id="e1d67-147">Pour utiliser les commutateurs de suivi, vous devez d’abord les créer et les placer dans votre code, comme décrit dans la section [Création et initialisation d’un commutateur de suivi](#create).</span><span class="sxs-lookup"><span data-stu-id="e1d67-147">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2. <span data-ttu-id="e1d67-148">Si votre projet ne contient pas de fichier de configuration (app.config ou Web.config), dans le menu **Projet**, sélectionnez **Ajouter un nouvel élément**.</span><span class="sxs-lookup"><span data-stu-id="e1d67-148">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    - <span data-ttu-id="e1d67-149">**Visual Basic** : dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez **Fichier de configuration de l’application**.</span><span class="sxs-lookup"><span data-stu-id="e1d67-149">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="e1d67-150">Le fichier de configuration de l'application est créé, puis ouvert.</span><span class="sxs-lookup"><span data-stu-id="e1d67-150">The application configuration file is created and opened.</span></span> <span data-ttu-id="e1d67-151">Il s'agit d'un document XML dont l'élément racine est `<configuration>.`</span><span class="sxs-lookup"><span data-stu-id="e1d67-151">This is an XML document whose root element is `<configuration>.`</span></span>  
  
    - <span data-ttu-id="e1d67-152">**Visual C#**  : dans la boîte de dialogue **Ajouter un nouvel élément**, choisissez **Fichier XML**.</span><span class="sxs-lookup"><span data-stu-id="e1d67-152">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="e1d67-153">Nommez ce fichier **app.config**. Dans l’éditeur XML, après la déclaration XML, ajoutez le code XML suivant :</span><span class="sxs-lookup"><span data-stu-id="e1d67-153">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="e1d67-154">Au moment de la compilation de votre projet, le fichier app.config est copié dans le dossier de sortie du projet et renommé *nom_application*.exe.config.</span><span class="sxs-lookup"><span data-stu-id="e1d67-154">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3. <span data-ttu-id="e1d67-155">Entre la balise `<configuration>` et la balise `</configuration>`, ajoutez le code XML approprié pour configurer vos commutateurs.</span><span class="sxs-lookup"><span data-stu-id="e1d67-155">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="e1d67-156">Les exemples suivants montrent un commutateur **BooleanSwitch** dont la propriété **DisplayName** a la valeur `DataMessageSwitch` et un commutateur **TraceSwitch** dont la propriété **DisplayName** a la valeur `TraceLevelSwitch`.</span><span class="sxs-lookup"><span data-stu-id="e1d67-156">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="e1d67-157">Dans cette configuration, les deux commutateurs sont désactivés.</span><span class="sxs-lookup"><span data-stu-id="e1d67-157">In this configuration, both switches are off.</span></span>  
  
4. <span data-ttu-id="e1d67-158">Si vous avez besoin d’activer un commutateur **BooleanSwitch**, tel que le commutateur `DataMessagesSwitch` montré dans l’exemple précédent, remplacez **Value** par un nombre entier différent de zéro (0).</span><span class="sxs-lookup"><span data-stu-id="e1d67-158">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5. <span data-ttu-id="e1d67-159">Si vous avez besoin d’activer un commutateur **TraceSwitch**, tel que le commutateur `TraceLevelSwitch` montré dans l’exemple précédent, remplacez **Value** par le paramètre correspondant au niveau approprié (1 à 4).</span><span class="sxs-lookup"><span data-stu-id="e1d67-159">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6. <span data-ttu-id="e1d67-160">Ajoutez des commentaires dans le fichier .config pour expliquer clairement à l'utilisateur quelles valeurs il doit modifier pour configurer les commutateurs de manière appropriée.</span><span class="sxs-lookup"><span data-stu-id="e1d67-160">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="e1d67-161">L'exemple suivant montre à quoi le code final, commentaires inclus, peut ressembler :</span><span class="sxs-lookup"><span data-stu-id="e1d67-161">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e1d67-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1d67-162">See also</span></span>

- [<span data-ttu-id="e1d67-163">Traçage et instrumentation d'applications</span><span class="sxs-lookup"><span data-stu-id="e1d67-163">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="e1d67-164">Comment : ajouter des instructions de traçage dans le code d'une application</span><span class="sxs-lookup"><span data-stu-id="e1d67-164">How to: Add Trace Statements to Application Code</span></span>](how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="e1d67-165">Commutateurs de traçage</span><span class="sxs-lookup"><span data-stu-id="e1d67-165">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="e1d67-166">Schéma des paramètres de traçage et de débogage</span><span class="sxs-lookup"><span data-stu-id="e1d67-166">Trace and Debug Settings Schema</span></span>](../configure-apps/file-schema/trace-debug/index.md)
