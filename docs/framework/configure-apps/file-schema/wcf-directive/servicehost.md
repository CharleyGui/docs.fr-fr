---
title: '@ServiceHost'
ms.date: 03/30/2017
ms.assetid: 96ba6967-00f2-422f-9aa7-15de4d33ebf3
ms.openlocfilehash: 3c7da8d5a473b801da8c48d1cb1504b95cc6c769
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75342129"
---
# <a name="servicehost"></a><span data-ttu-id="1afa1-101">\@ServiceHost</span><span class="sxs-lookup"><span data-stu-id="1afa1-101">\@ServiceHost</span></span>
<span data-ttu-id="1afa1-102">Associe la fabrique utilisée pour générer l'hôte de service au service à héberger ainsi qu'à d'autres aspects de programmation requis pour compiler le code d'hébergement fourni dans le fichier .svc ou pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="1afa1-102">Associates the factory used to produce the service host with the service to be hosted and other programming aspects required to access or compile the hosting code provided in the .svc file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1afa1-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1afa1-103">Syntax</span></span>  
  
```xml  
<% @ServiceHost
Service = "Service, ServiceNamespace"
Factory = "Factory, FactoryNamespace"
Debug = "Debug"
Language = "Language"
CodeBehind = "CodeBehind"
%>
```  
  
## <a name="attributes"></a><span data-ttu-id="1afa1-104">Attributs</span><span class="sxs-lookup"><span data-stu-id="1afa1-104">Attributes</span></span>  
  
#### <a name="service"></a><span data-ttu-id="1afa1-105">Service</span><span class="sxs-lookup"><span data-stu-id="1afa1-105">Service</span></span>  
 <span data-ttu-id="1afa1-106">Nom de type CLR du service hébergé.</span><span class="sxs-lookup"><span data-stu-id="1afa1-106">The CLR type name of the service hosted.</span></span> <span data-ttu-id="1afa1-107">Il doit s'agir d'un nom qualifié correspondant à un type qui implémente un ou plusieurs contacts du service.</span><span class="sxs-lookup"><span data-stu-id="1afa1-107">This should be a qualified name of a type that implements one or more of the service contacts.</span></span>  
  
#### <a name="factory"></a><span data-ttu-id="1afa1-108">Fabrique</span><span class="sxs-lookup"><span data-stu-id="1afa1-108">Factory</span></span>  
 <span data-ttu-id="1afa1-109">Nom de type CLR correspondant à la fabrique de l'hôte de service utilisée pour instancier l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="1afa1-109">The CLR type name of the service host factory used to instantiate the service host.</span></span> <span data-ttu-id="1afa1-110">Cet attribut est facultatif.</span><span class="sxs-lookup"><span data-stu-id="1afa1-110">This attribute is optional.</span></span> <span data-ttu-id="1afa1-111">S'il n'est pas spécifié, le <xref:System.ServiceModel.Activation.ServiceHostFactory> par défaut est utilisé et renvoie une instance de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1afa1-111">If unspecified, the default <xref:System.ServiceModel.Activation.ServiceHostFactory> is used, which returns an instance of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
#### <a name="debug"></a><span data-ttu-id="1afa1-112">Déboguer</span><span class="sxs-lookup"><span data-stu-id="1afa1-112">Debug</span></span>  
 <span data-ttu-id="1afa1-113">Indique si le service Windows Communication Foundation (WCF) doit être compilé avec des symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="1afa1-113">Indicates whether the Windows Communication Foundation (WCF) service should be compiled with debug symbols.</span></span> <span data-ttu-id="1afa1-114">`true` si le service WCF doit être compilé avec des symboles de débogage ; Sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="1afa1-114">`true` if the WCF service should be compiled with debug symbols; otherwise, `false`.</span></span>  
  
#### <a name="language"></a><span data-ttu-id="1afa1-115">Language</span><span class="sxs-lookup"><span data-stu-id="1afa1-115">Language</span></span>  
 <span data-ttu-id="1afa1-116">Spécifie le langage utilisé lors de la compilation de l'intégralité du code incorporé dans le fichier (.svc).</span><span class="sxs-lookup"><span data-stu-id="1afa1-116">Specifies the language used when compiling all the inline code within file (.svc).</span></span> <span data-ttu-id="1afa1-117">Les valeurs peuvent représenter any. Langage NET-pris en charge, y compris `C#`, `VB`et `JS`, qui C#font respectivement référence à, Visual Basic et JScript .net.</span><span class="sxs-lookup"><span data-stu-id="1afa1-117">The values can represent any .NET-supported language, including `C#`, `VB`, and `JS`, which refer to C#, Visual Basic, and JScript .NET, respectively.</span></span> <span data-ttu-id="1afa1-118">Cet attribut est facultatif.</span><span class="sxs-lookup"><span data-stu-id="1afa1-118">This attribute is optional.</span></span>  
  
#### <a name="codebehind"></a><span data-ttu-id="1afa1-119">CodeBehind</span><span class="sxs-lookup"><span data-stu-id="1afa1-119">CodeBehind</span></span>  
 <span data-ttu-id="1afa1-120">Spécifie le fichier source qui implémente le service web XML, lorsque la classe implémentant le service web XML ne réside pas dans le même fichier et n’a pas été compilée dans un assembly et placée dans le répertoire \Bin.</span><span class="sxs-lookup"><span data-stu-id="1afa1-120">Specifies the source file that implements the XML Web service, when the class that implements the XML Web service does not reside in the same file and has not been compiled into an assembly and placed in the \Bin directory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1afa1-121">Notes</span><span class="sxs-lookup"><span data-stu-id="1afa1-121">Remarks</span></span>  
 <span data-ttu-id="1afa1-122">Le <xref:System.ServiceModel.ServiceHost> utilisé pour héberger le service est un point d’extensibilité au sein du modèle de programmation Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1afa1-122">The <xref:System.ServiceModel.ServiceHost> used to host the service is a point of extensibility within the Windows Communication Foundation (WCF) programming model.</span></span> <span data-ttu-id="1afa1-123">Un modèle de fabrique est utilisé pour instancier le <xref:System.ServiceModel.ServiceHost> car il peut s'agir d'un type polymorphe ne devant pas être instancié directement par l'environnement d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="1afa1-123">A factory pattern is used to instantiate the <xref:System.ServiceModel.ServiceHost> because it is, potentially, a polymorphic type that the hosting environment should not instantiate directly.</span></span>  
  
 <span data-ttu-id="1afa1-124">L'implémentation par défaut utilise <xref:System.ServiceModel.Activation.ServiceHostFactory> pour créer une instance de <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="1afa1-124">The default implementation uses <xref:System.ServiceModel.Activation.ServiceHostFactory> to create an instance of <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="1afa1-125">Toutefois, vous pouvez fournir votre propre fabrique (un qui retourne votre hôte dérivé) en spécifiant le nom de type CLR de votre implémentation de fabrique dans la directive [\@ServiceHost](servicehost.md) .</span><span class="sxs-lookup"><span data-stu-id="1afa1-125">But you can provide your own factory (one that returns your derived host) by specifying the CLR type name of your factory implementation in the [\@ServiceHost](servicehost.md) directive.</span></span>  
  
 <span data-ttu-id="1afa1-126">Pour utiliser votre propre fabrique d’hôte de service personnalisée au lieu de la fabrique par défaut, il vous suffit de fournir le nom de type dans la directive [@ServiceHost](servicehost.md) comme suit :</span><span class="sxs-lookup"><span data-stu-id="1afa1-126">To use you own custom service host factory instead of the default factory, just provide the type name in the [@ServiceHost](servicehost.md) directive as follows:</span></span>  
  
```xml  
<% @ServiceHost Factory="DerivedFactory" Service="MyService" %>  
```  
  
 <span data-ttu-id="1afa1-127">Surchargez les implémentations de fabrique le moins possible.</span><span class="sxs-lookup"><span data-stu-id="1afa1-127">Keep the factory implementations as light as possible.</span></span> <span data-ttu-id="1afa1-128">Si vous disposez d'une importante logique personnalisée, votre code est plus facilement réutilisable si vous intégrez cette logique à votre hôte et non à la fabrique.</span><span class="sxs-lookup"><span data-stu-id="1afa1-128">If you have lots of custom logic, your code is more reusable if you put that logic inside your host instead of inside the factory.</span></span>  
  
 <span data-ttu-id="1afa1-129">Par exemple, pour activer un point de terminaison compatible AJAX pour `MyService`, spécifiez le <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> pour la valeur de l’attribut `Factory`, au lieu du <xref:System.ServiceModel.Activation.ServiceHostFactory>par défaut, dans la directive [@ServiceHost](servicehost.md) comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="1afa1-129">For example, to enable an AJAX-enabled endpoint for `MyService`, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> for the value of the `Factory` attribute, instead of the default <xref:System.ServiceModel.Activation.ServiceHostFactory>, in the [@ServiceHost](servicehost.md) directive as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1afa1-130">Exemple</span><span class="sxs-lookup"><span data-stu-id="1afa1-130">Example</span></span>  
  
```xml  
<% @ServiceHost
Service="MyService"  
Language="C#"  
Debug="true"  
Factory="WebScriptServiceHostFactory"  
%>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1afa1-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1afa1-131">See also</span></span>

- [<span data-ttu-id="1afa1-132">Hôte de service personnalisé</span><span class="sxs-lookup"><span data-stu-id="1afa1-132">Custom Service Host</span></span>](../../../wcf/samples/custom-service-host.md)
