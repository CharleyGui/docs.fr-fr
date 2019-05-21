---
title: Accès aux membres non exposés sur le modèle objet de document HTML managé
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- unexposed members
- managed HTML DOM [Windows Forms], accessing unexposed members
ms.assetid: 762295bd-2355-4aa7-b43c-5bff997a33e6
ms.openlocfilehash: 539ac998a557615c097c33cdd4207e99f396e81d
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959628"
---
# <a name="accessing-unexposed-members-on-the-managed-html-document-object-model"></a><span data-ttu-id="feeff-102">Accès aux membres non exposés sur le modèle objet de document HTML managé</span><span class="sxs-lookup"><span data-stu-id="feeff-102">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>
<span data-ttu-id="feeff-103">Le DOM HTML managé Document objet Model () contient une classe appelée <xref:System.Windows.Forms.HtmlElement> qui expose des propriétés, méthodes et événements de tous les éléments HTML ont en commun.</span><span class="sxs-lookup"><span data-stu-id="feeff-103">The managed HTML Document Object Model (DOM) contains a class called <xref:System.Windows.Forms.HtmlElement> that exposes the properties, methods, and events that all HTML elements have in common.</span></span> <span data-ttu-id="feeff-104">Parfois, cependant, vous devez accéder aux membres de l’interface managée n’expose pas directement.</span><span class="sxs-lookup"><span data-stu-id="feeff-104">Sometimes, however, you will need to access members that the managed interface does not directly expose.</span></span> <span data-ttu-id="feeff-105">Cette rubrique examine deux façons d’accéder aux membres non exposés, y compris les fonctions JScript et VBScript définies à l’intérieur d’une page Web.</span><span class="sxs-lookup"><span data-stu-id="feeff-105">This topic examines two ways for accessing unexposed members, including JScript and VBScript functions defined inside of a Web page.</span></span>  
  
## <a name="accessing-unexposed-members-through-managed-interfaces"></a><span data-ttu-id="feeff-106">L’accès aux membres non exposés via des Interfaces managées</span><span class="sxs-lookup"><span data-stu-id="feeff-106">Accessing Unexposed Members through Managed Interfaces</span></span>  
 <span data-ttu-id="feeff-107"><xref:System.Windows.Forms.HtmlDocument> et <xref:System.Windows.Forms.HtmlElement> fournissent quatre méthodes qui permettent l’accès aux membres non exposés.</span><span class="sxs-lookup"><span data-stu-id="feeff-107"><xref:System.Windows.Forms.HtmlDocument> and <xref:System.Windows.Forms.HtmlElement> provide four methods that enable access to unexposed members.</span></span> <span data-ttu-id="feeff-108">Le tableau suivant présente les types et leurs méthodes correspondantes.</span><span class="sxs-lookup"><span data-stu-id="feeff-108">The following table shows the types and their corresponding methods.</span></span>  
  
|<span data-ttu-id="feeff-109">Type de membre</span><span class="sxs-lookup"><span data-stu-id="feeff-109">Member Type</span></span>|<span data-ttu-id="feeff-110">Méthode (s)</span><span class="sxs-lookup"><span data-stu-id="feeff-110">Method(s)</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="feeff-111">Propriétés (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="feeff-111">Properties (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.GetAttribute%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.SetAttribute%2A>|  
|<span data-ttu-id="feeff-112">Méthodes</span><span class="sxs-lookup"><span data-stu-id="feeff-112">Methods</span></span>|<xref:System.Windows.Forms.HtmlElement.InvokeMember%2A>|  
|<span data-ttu-id="feeff-113">Événements (<xref:System.Windows.Forms.HtmlDocument>)</span><span class="sxs-lookup"><span data-stu-id="feeff-113">Events (<xref:System.Windows.Forms.HtmlDocument>)</span></span>|<xref:System.Windows.Forms.HtmlDocument.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlDocument.DetachEventHandler%2A>|  
|<span data-ttu-id="feeff-114">Événements (<xref:System.Windows.Forms.HtmlElement>)</span><span class="sxs-lookup"><span data-stu-id="feeff-114">Events (<xref:System.Windows.Forms.HtmlElement>)</span></span>|<xref:System.Windows.Forms.HtmlElement.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlElement.DetachEventHandler%2A>|  
|<span data-ttu-id="feeff-115">Événements (<xref:System.Windows.Forms.HtmlWindow>)</span><span class="sxs-lookup"><span data-stu-id="feeff-115">Events (<xref:System.Windows.Forms.HtmlWindow>)</span></span>|<xref:System.Windows.Forms.HtmlWindow.AttachEventHandler%2A><br /><br /> <xref:System.Windows.Forms.HtmlWindow.DetachEventHandler%2A>|  
  
 <span data-ttu-id="feeff-116">Lorsque vous utilisez ces méthodes, il est supposé que vous disposez d’un élément du type sous-jacent correct.</span><span class="sxs-lookup"><span data-stu-id="feeff-116">When you use these methods, it is assumed that you have an element of the correct underlying type.</span></span> <span data-ttu-id="feeff-117">Supposons que vous souhaitez écouter le `Submit` événement d’un `FORM` page de l’élément sur un élément HTML, afin que vous pouvez effectuer un prétraitement sur le `FORM`de valeurs avant que l’utilisateur les soumet au serveur.</span><span class="sxs-lookup"><span data-stu-id="feeff-117">Suppose that you want to listen to the `Submit` event of a `FORM` element on an HTML page, so that you can perform some pre-processing on the `FORM`'s values before the user submits them to the server.</span></span> <span data-ttu-id="feeff-118">Dans l’idéal, si vous contrôlez le code HTML, vous devez définir le `FORM` pour avoir une valeur unique `ID` attribut.</span><span class="sxs-lookup"><span data-stu-id="feeff-118">Ideally, if you have control over the HTML, you would define the `FORM` to have a unique `ID` attribute.</span></span>  
  
```  
<HTML>  
  
    <HEAD>  
        <TITLE>Form Page</TITLE>  
    </HEAD>  
  
    <BODY>  
        <FORM ID="form1">  
             ... form fields defined here ...  
        </FORM>  
    </BODY>  
  
</HTML>  
```  
  
 <span data-ttu-id="feeff-119">Une fois que vous chargez cette page dans le <xref:System.Windows.Forms.WebBrowser> contrôle, vous pouvez utiliser la <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> méthode pour récupérer le `FORM` au moment de l’exécution à l’aide `form1` comme argument.</span><span class="sxs-lookup"><span data-stu-id="feeff-119">After you load this page into the <xref:System.Windows.Forms.WebBrowser> control, you can use the <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A> method to retrieve the `FORM` at run time using `form1` as the argument.</span></span>  
  
 [!code-csharp[System.Windows.Forms.HtmlElement#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/CS/Form1.cs#10)]
 [!code-vb[System.Windows.Forms.HtmlElement#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.HtmlElement/VB/Form1.vb#10)]  
  
## <a name="accessing-unmanaged-interfaces"></a><span data-ttu-id="feeff-120">L’accès à des Interfaces non managées</span><span class="sxs-lookup"><span data-stu-id="feeff-120">Accessing Unmanaged Interfaces</span></span>  
 <span data-ttu-id="feeff-121">Vous pouvez également accéder à des membres non exposés sur le DOM HTML managé en utilisant les interfaces de composant COM (Object Model) non managées exposées par chaque classe DOM.</span><span class="sxs-lookup"><span data-stu-id="feeff-121">You can also access unexposed members on the managed HTML DOM by using the unmanaged Component Object Model (COM) interfaces exposed by each DOM class.</span></span> <span data-ttu-id="feeff-122">Cela est recommandé si vous devez effectuer plusieurs appels par rapport aux membres non exposés, ou si les membres non exposés retournent d’autres interfaces non managées ne pas encapsulées par le DOM. HTML managé</span><span class="sxs-lookup"><span data-stu-id="feeff-122">This is recommended if you have to make several calls against unexposed members, or if the unexposed members return other unmanaged interfaces not wrapped by the managed HTML DOM.</span></span>  
  
 <span data-ttu-id="feeff-123">Le tableau suivant montre toutes les interfaces non managées exposées via le DOM. HTML managé</span><span class="sxs-lookup"><span data-stu-id="feeff-123">The following table shows all of the unmanaged interfaces exposed through the managed HTML DOM.</span></span> <span data-ttu-id="feeff-124">Cliquez sur chaque lien pour obtenir une explication de son utilisation et par exemple de code.</span><span class="sxs-lookup"><span data-stu-id="feeff-124">Click on each link for an explanation of its usage and for example code.</span></span>  
  
|<span data-ttu-id="feeff-125">Type</span><span class="sxs-lookup"><span data-stu-id="feeff-125">Type</span></span>|<span data-ttu-id="feeff-126">Interface non managée</span><span class="sxs-lookup"><span data-stu-id="feeff-126">Unmanaged Interface</span></span>|  
|----------|-------------------------|  
|<xref:System.Windows.Forms.HtmlDocument>|<xref:System.Windows.Forms.HtmlDocument.DomDocument%2A>|  
|<xref:System.Windows.Forms.HtmlElement>|<xref:System.Windows.Forms.HtmlElement.DomElement%2A>|  
|<xref:System.Windows.Forms.HtmlWindow>|<xref:System.Windows.Forms.HtmlWindow.DomWindow%2A>|  
|<xref:System.Windows.Forms.HtmlHistory>|<xref:System.Windows.Forms.HtmlHistory.DomHistory%2A>|  
  
 <span data-ttu-id="feeff-127">Le moyen le plus simple d’utiliser les interfaces COM consiste à ajouter une référence à la bibliothèque DOM HTML non managée (MSHTML.dll) à partir de votre application, bien que cela soit non pris en charge.</span><span class="sxs-lookup"><span data-stu-id="feeff-127">The easiest way to use the COM interfaces is to add a reference to the unmanaged HTML DOM library (MSHTML.dll) from your application, although this is unsupported.</span></span> <span data-ttu-id="feeff-128">Pour plus d’informations, consultez [934368 d’Article de Base de connaissances](https://support.microsoft.com/kb/934368).</span><span class="sxs-lookup"><span data-stu-id="feeff-128">For more information, see [Knowledge Base Article 934368](https://support.microsoft.com/kb/934368).</span></span>  
  
## <a name="accessing-script-functions"></a><span data-ttu-id="feeff-129">L’accès aux fonctions de Script</span><span class="sxs-lookup"><span data-stu-id="feeff-129">Accessing Script Functions</span></span>  
 <span data-ttu-id="feeff-130">Une page HTML peut définir une ou plusieurs fonctions à l’aide d’un langage de script tels que JScript ou VBScript.</span><span class="sxs-lookup"><span data-stu-id="feeff-130">An HTML page can define one or more functions by using a scripting language such as JScript or VBScript.</span></span> <span data-ttu-id="feeff-131">Ces fonctions sont placées à l’intérieur d’un `SCRIPT` page dans la page et peut être exécuté à la demande ou en réponse à un événement sur le DOM.</span><span class="sxs-lookup"><span data-stu-id="feeff-131">These functions are placed inside of a `SCRIPT` page in the page, and can be run on demand or in response to an event on the DOM.</span></span>  
  
 <span data-ttu-id="feeff-132">Vous pouvez appeler des fonctions de script que vous définissez dans une page HTML à l’aide du <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="feeff-132">You can call any script functions you define in an HTML page using the <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A> method.</span></span> <span data-ttu-id="feeff-133">Si la méthode de script retourne un élément HTML, vous pouvez utiliser un cast pour convertir ce résultat en un <xref:System.Windows.Forms.HtmlElement>.</span><span class="sxs-lookup"><span data-stu-id="feeff-133">If the script method returns an HTML element, you can use a cast to convert this return result to an <xref:System.Windows.Forms.HtmlElement>.</span></span> <span data-ttu-id="feeff-134">Pour plus d’informations et des exemples de code, consultez <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span><span class="sxs-lookup"><span data-stu-id="feeff-134">For details and example code, see <xref:System.Windows.Forms.HtmlDocument.InvokeScript%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feeff-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feeff-135">See also</span></span>

- [<span data-ttu-id="feeff-136">Utilisation du modèle DOM HTML managé</span><span class="sxs-lookup"><span data-stu-id="feeff-136">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
