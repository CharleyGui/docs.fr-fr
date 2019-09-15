---
title: 'Procédure : utiliser un moniker de service avec des contrats d’échange de métadonnées'
ms.date: 03/30/2017
ms.assetid: c41a07e5-cb9d-45d6-9ea4-34511e227faf
ms.openlocfilehash: e114bc2c046ba7145a91121ce23c82912680a048
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968961"
---
# <a name="how-to-use-a-service-moniker-with-metadata-exchange-contracts"></a><span data-ttu-id="6ceb3-102">Procédure : utiliser un moniker de service avec des contrats d’échange de métadonnées</span><span class="sxs-lookup"><span data-stu-id="6ceb3-102">How to: Use a Service Moniker with Metadata Exchange Contracts</span></span>
<span data-ttu-id="6ceb3-103">Après avoir développé de nouveaux services WCF, vous pouvez décider que vous souhaitez être en mesure d’appeler ces services à partir d’un script ou d’une application Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-103">After developing some new WCF services, you may decide that you want to be able to call these services from a script or a Visual Basic 6.0 application.</span></span> <span data-ttu-id="6ceb3-104">Une méthode consisterait à générer un assembly client WCF, à inscrire l’assembly auprès de COM, à installer l’assembly dans le GAC, puis à référencer les types COM à partir de votre code Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-104">One method would be to generate a WCF client assembly, register the assembly with COM, install the assembly in the GAC, and then reference the COM types from your Visual Basic code.</span></span> <span data-ttu-id="6ceb3-105">Lorsque vous distribuez l’application, vous devez également distribuer l’assembly client WCF.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-105">When you distribute the application, you will have to distribute the WCF Client assembly as well.</span></span> <span data-ttu-id="6ceb3-106">L'utilisateur devra ensuite inscrire l'assembly client WCF avec COM et le placer dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-106">The user will then have to register the WCF client assembly with COM and place it in the GAC.</span></span> <span data-ttu-id="6ceb3-107">L’interopérabilité COM WCF vous permet également d’effectuer les mêmes appels de service sans compter sur un assembly client WCF.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-107">WCF COM Interop also allows you to make the same service calls without relying on a WCF client assembly.</span></span> <span data-ttu-id="6ceb3-108">Le moniker WCF vous permet d’appeler n’importe quel service WCF à partir de n’importe quel langage compatible COM (Visual Basic, VBScript, Visual Basic pour Applications (VBA), etc.) en spécifiant un URI de point de terminaison MEX (Metadata Exchange) que le moniker de service utilise pour extraire le type informations sur le service.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-108">The WCF moniker allows you to call any WCF service from any COM-compatible language (Visual Basic, VBScript, Visual Basic for Applications (VBA), and so on) by specifying a metadata exchange (Mex) endpoint URI that the service moniker uses to extract type information about the service.</span></span> <span data-ttu-id="6ceb3-109">Cette rubrique explique comment appeler l’exemple WCF Prise en main à l’aide d’un moniker WCF qui spécifie un point de terminaison MEX.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-109">This topic describes how to call the Getting Started WCF sample using a WCF moniker that specifies a Mex endpoint.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ceb3-110">Les types définis par l’assembly client WCF ne sont jamais instanciés en fait.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-110">The types defined by the WCF client assembly are never actually instantiated.</span></span> <span data-ttu-id="6ceb3-111">L'assembly est utilisé uniquement pour les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-111">The assembly is used only for metadata.</span></span>  
  
### <a name="using-the-service-moniker-with-a-mex-address"></a><span data-ttu-id="6ceb3-112">Utilisation du moniker de service avec une adresse Mex</span><span class="sxs-lookup"><span data-stu-id="6ceb3-112">Using the service moniker with a Mex address</span></span>  
  
1. <span data-ttu-id="6ceb3-113">Générez l’exemple de prise en main et utilisez Internet Explorer pour accéder à son http://localhost/ServiceModelSamples/Service.svc) URL (pour vous assurer que le service fonctionne.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-113">Build the Getting Started sample and use Internet Explorer to browse to its URL (http://localhost/ServiceModelSamples/Service.svc) to ensure that the service is working.</span></span>  
  
2. <span data-ttu-id="6ceb3-114">Créez un script Visual Basic ou une application Visual Basic qui contient le code suivant :</span><span class="sxs-lookup"><span data-stu-id="6ceb3-114">Create a Visual Basic script or Visual Basic application that contains the following code:</span></span>  
  
    ```vb
    monString = "service:mexaddress=http://localhost/ServiceModelSamples/Service.svc/MEX"  
    monString = monString + ", address=http://localhost/ServiceModelSamples/Service.svc"  
    monString = monString + ", contract=ICalculator, contractNamespace=http://Microsoft.ServiceModel.Samples"  
    monString = monString + ", binding=WSHttpBinding_ICalculator, bindingNamespace=http://Microsoft.ServiceModel.Samples"  
  
    Set calc = GetObject(monString)  
    MsgBox calc.Add(3, 4)  
    ```  
  
3. <span data-ttu-id="6ceb3-115">Exécutez l'application ou le script Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-115">Run the Visual Basic application or script.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6ceb3-116">Le service que vous appelez doit exposer un point de terminaison Mex pour que le moniker soit en mesure de lire les métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-116">The service you are calling must expose a Mex endpoint for the moniker to be able to read the metadata from the service.</span></span> <span data-ttu-id="6ceb3-117">Pour plus d’informations, consultez [Guide pratique pour Publier les métadonnées d’un service à l'](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)aide d’un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-117">For more information, see [How to: Publish Metadata for a Service Using a Configuration File](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="6ceb3-118">Si le moniker est mal formé ou si le service n'est pas disponible, l'appel à `GetObject` retourne une erreur indiquant que la syntaxe n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-118">If the moniker is malformed or if the service is unavailable, the call to `GetObject` will return an error saying "Invalid Syntax."</span></span>  <span data-ttu-id="6ceb3-119">Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.</span><span class="sxs-lookup"><span data-stu-id="6ceb3-119">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ceb3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6ceb3-120">See also</span></span>

- [<span data-ttu-id="6ceb3-121">Guide pratique : Utiliser le moniker du service Windows Communication Foundation sans inscription</span><span class="sxs-lookup"><span data-stu-id="6ceb3-121">How to: Use the Windows Communication Foundation Service Moniker without Registration</span></span>](../../../../docs/framework/wcf/feature-details/use-the-wcf-service-moniker-without-registration.md)
- [<span data-ttu-id="6ceb3-122">Guide pratique : Utiliser un moniker de service avec des contrats WSDL</span><span class="sxs-lookup"><span data-stu-id="6ceb3-122">How to: Use a Service Moniker with WSDL Contracts</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-service-moniker-with-wsdl-contracts.md)
