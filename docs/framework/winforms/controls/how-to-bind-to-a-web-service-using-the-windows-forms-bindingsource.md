---
title: Liaison à un service Web à l’aide de BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Web services [Windows Forms], binding controls
- BindingSource component [Windows Forms], binding to a Web service
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to Web service
- BindingSource component [Windows Forms], examples
ms.assetid: ee261207-4573-4cb9-a8cb-5185037e0fba
ms.openlocfilehash: 0680c73e578577cf40158761f6c635fe30ff9f4d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746683"
---
# <a name="how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource"></a><span data-ttu-id="9aa61-102">Comment : établir une liaison à un service Web à l’aide du BindingSource Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9aa61-102">How to: Bind to a Web Service Using the Windows Forms BindingSource</span></span>
<span data-ttu-id="9aa61-103">Si vous voulez lier un contrôle Windows Forms aux résultats obtenus à partir d'un appel à un service web XML, vous pouvez utiliser un composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="9aa61-103">If you want to bind a Windows Form control to the results obtained from calling an XML Web service, you can use a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="9aa61-104">Cette procédure est similaire à celle d'une liaison d'un composant <xref:System.Windows.Forms.BindingSource> à un type.</span><span class="sxs-lookup"><span data-stu-id="9aa61-104">This procedure is similar to binding a <xref:System.Windows.Forms.BindingSource> component to a type.</span></span> <span data-ttu-id="9aa61-105">Vous devez créer un proxy côté client qui contienne les méthodes et les types exposés par le service web.</span><span class="sxs-lookup"><span data-stu-id="9aa61-105">You must create a client-side proxy that contains the methods and types exposed by the Web service.</span></span> <span data-ttu-id="9aa61-106">Vous générez un proxy côté client à partir du service web (.asmx) lui-même ou à partir de son fichier WSDL.</span><span class="sxs-lookup"><span data-stu-id="9aa61-106">You generate a client-side proxy from the Web service (.asmx) itself, or its Web Services Description Language (WSDL) file.</span></span> <span data-ttu-id="9aa61-107">En outre, votre proxy côté client doit exposer les champs de types complexes utilisés par le service web en tant que propriétés publiques.</span><span class="sxs-lookup"><span data-stu-id="9aa61-107">Additionally, your client-side proxy must expose the fields of complex types used by the Web service as public properties.</span></span> <span data-ttu-id="9aa61-108">Vous pouvez ensuite lier la <xref:System.Windows.Forms.BindingSource> à l'un des types exposés dans le proxy du service web.</span><span class="sxs-lookup"><span data-stu-id="9aa61-108">You then bind the <xref:System.Windows.Forms.BindingSource> to one of the types exposed in the Web service proxy.</span></span>  
  
### <a name="to-create-and-bind-to-a-client-side-proxy"></a><span data-ttu-id="9aa61-109">Pour créer un proxy côté client et créer des liaisons à celui-ci</span><span class="sxs-lookup"><span data-stu-id="9aa61-109">To create and bind to a client-side proxy</span></span>  
  
1. <span data-ttu-id="9aa61-110">Créez un formulaire Windows dans le répertoire de votre choix, avec un espace de noms approprié.</span><span class="sxs-lookup"><span data-stu-id="9aa61-110">Create a Windows Form in the directory of your choice, with an appropriate namespace.</span></span>  
  
2. <span data-ttu-id="9aa61-111">Ajoutez un composant <xref:System.Windows.Forms.BindingSource> au formulaire.</span><span class="sxs-lookup"><span data-stu-id="9aa61-111">Add a <xref:System.Windows.Forms.BindingSource> component to the form.</span></span>  
  
3. <span data-ttu-id="9aa61-112">Ouvrez l’invite de commandes du kit de développement logiciel (SDK) Windows et accédez au même répertoire que celui dans lequel se trouve votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="9aa61-112">Open the Windows Software Development Kit (SDK) command prompt, and navigate to the same directory that your form is located in.</span></span>  
  
4. <span data-ttu-id="9aa61-113">À l’aide de l’outil WSDL, entrez `wsdl` et l’URL du fichier .asmx ou WSDL du service web, suivi de l’espace de noms de votre application, et éventuellement le langage utilisé.</span><span class="sxs-lookup"><span data-stu-id="9aa61-113">Using the WSDL tool, enter `wsdl` and the URL for the .asmx or WSDL file for the Web service, followed by the namespace of your application, and optionally the language you are working in.</span></span>  
  
     <span data-ttu-id="9aa61-114">L’exemple de code suivant utilise le service Web situé dans `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span><span class="sxs-lookup"><span data-stu-id="9aa61-114">The following code example uses the Web service located at `http://webservices.eraserver.net/zipcoderesolver/zipcoderesolver.asmx`.</span></span> <span data-ttu-id="9aa61-115">Par exemple, pour un type C# `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService` ou pour un type Visual Basic `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span><span class="sxs-lookup"><span data-stu-id="9aa61-115">For example, for C# type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService`, or for Visual Basic type `wsdl http://webservices.eraserver.net.zipcoderesolver/zipcoderesolver.asmx /n:BindToWebService /language:VB`.</span></span> <span data-ttu-id="9aa61-116">Le fait de passer le chemin d’accès en tant qu’argument à l’outil WSDL génère un proxy côté client dans le même répertoire et le même espace de noms que votre application, dans le langage spécifié.</span><span class="sxs-lookup"><span data-stu-id="9aa61-116">Passing the path as an argument to the WSDL tool will generate a client-side proxy in the same directory and namespace as your application, in the specified language.</span></span> <span data-ttu-id="9aa61-117">Si vous utilisez Visual Studio, ajoutez le fichier à votre projet.</span><span class="sxs-lookup"><span data-stu-id="9aa61-117">If you are using Visual Studio, add the file to your project.</span></span>  
  
5. <span data-ttu-id="9aa61-118">Sélectionnez un type dans le proxy côté client avec lequel créer une liaison.</span><span class="sxs-lookup"><span data-stu-id="9aa61-118">Select a type in the client-side proxy to bind to.</span></span>  
  
     <span data-ttu-id="9aa61-119">Il s'agit généralement d'un type retourné par une méthode fournie par le service web.</span><span class="sxs-lookup"><span data-stu-id="9aa61-119">This is typically a type returned by a method offered by the Web service.</span></span> <span data-ttu-id="9aa61-120">Les champs du type choisi doivent être exposés en tant que propriétés publiques pour la liaison.</span><span class="sxs-lookup"><span data-stu-id="9aa61-120">The fields of the chosen type must be exposed as public properties for binding purposes.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#4)]  
  
6. <span data-ttu-id="9aa61-121">Définissez la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> de <xref:System.Windows.Forms.BindingSource> sur le type contenu dans le proxy côté client du service web.</span><span class="sxs-lookup"><span data-stu-id="9aa61-121">Set the <xref:System.Windows.Forms.BindingSource.DataSource%2A> property of the <xref:System.Windows.Forms.BindingSource> to the type you want that is contained in the Web service client-side proxy.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#2)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#2)]  
  
### <a name="to-bind-controls-to-the-bindingsource-that-is-bound-to-a-web-service"></a><span data-ttu-id="9aa61-122">Pour lier des contrôles à une BindingSource liée à un service web</span><span class="sxs-lookup"><span data-stu-id="9aa61-122">To bind controls to the BindingSource that is bound to a Web service</span></span>  
  
- <span data-ttu-id="9aa61-123">Liez des contrôles à <xref:System.Windows.Forms.BindingSource>, en passant la propriété publique du type de service web de votre choix en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="9aa61-123">Bind controls to the <xref:System.Windows.Forms.BindingSource>, passing the public property of the Web service type that you want as a parameter.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#3)]
     [!code-csharp[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.DataConnectorWebService#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="9aa61-124">Exemple</span><span class="sxs-lookup"><span data-stu-id="9aa61-124">Example</span></span>  
 <span data-ttu-id="9aa61-125">L'exemple de code suivant montre comment lier un composant <xref:System.Windows.Forms.BindingSource> à un service web, puis comment lier une zone de texte au composant <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="9aa61-125">The following code example demonstrates how to bind a <xref:System.Windows.Forms.BindingSource> component to a Web service, and then how to bind a text box to the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="9aa61-126">Quand vous cliquez sur le bouton, une méthode de service web est appelée et les résultats s'affichent dans `textbox1`.</span><span class="sxs-lookup"><span data-stu-id="9aa61-126">When you click the button, a Web service method is called and the results will appear in `textbox1`.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorWebService#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorWebService/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9aa61-127">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="9aa61-127">Compiling the Code</span></span>  
 <span data-ttu-id="9aa61-128">Il s'agit d'un exemple complet qui inclut une méthode `Main` et une version raccourcie du code du proxy côté client.</span><span class="sxs-lookup"><span data-stu-id="9aa61-128">This is a complete example that includes a `Main` method, and a shortened version of client-side proxy code.</span></span>  
  
 <span data-ttu-id="9aa61-129">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="9aa61-129">This example requires:</span></span>  
  
- <span data-ttu-id="9aa61-130">Des références aux assemblys System, System.Drawing, System.Web.Services, System.Windows.Forms et System.Xml.</span><span class="sxs-lookup"><span data-stu-id="9aa61-130">References to the System, System.Drawing, System.Web.Services, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9aa61-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9aa61-131">See also</span></span>

- [<span data-ttu-id="9aa61-132">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="9aa61-132">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="9aa61-133">Comment : lier un contrôle Windows Forms à un type</span><span class="sxs-lookup"><span data-stu-id="9aa61-133">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
