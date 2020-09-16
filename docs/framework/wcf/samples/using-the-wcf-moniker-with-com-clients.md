---
title: Using the WCF Moniker with COM Clients
ms.date: 03/30/2017
ms.assetid: e2799bfe-88bd-49d7-9d6d-ac16a9b16b04
ms.openlocfilehash: b36b646f650c2a2974c7b0689a9367961075ea14
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553017"
---
# <a name="using-the-wcf-moniker-with-com-clients"></a><span data-ttu-id="b40e1-102">Using the WCF Moniker with COM Clients</span><span class="sxs-lookup"><span data-stu-id="b40e1-102">Using the WCF Moniker with COM Clients</span></span>
<span data-ttu-id="b40e1-103">Cet exemple montre comment utiliser le moniker de service Windows Communication Foundation (WCF) pour intégrer des services Web dans des environnements de développement COM, tels que Microsoft Office Visual Basic pour Applications (Office VBA) ou Visual Basic 6,0.</span><span class="sxs-lookup"><span data-stu-id="b40e1-103">This sample demonstrates how to use the Windows Communication Foundation (WCF) service moniker to integrate Web services into COM-based development environments, such as Microsoft Office Visual Basic for Applications (Office VBA) or Visual Basic 6.0.</span></span> <span data-ttu-id="b40e1-104">Il se compose d'un client Windows Script Host (.vbs), d'une bibliothèque de client assurant la prise en charge (.dll) et d'une bibliothèque de service (.dll) hébergée par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="b40e1-104">This sample consists of a Windows Script Host client (.vbs), a supporting client library (.dll), and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b40e1-105">Le service correspond à un service de calculatrice et le client COM appelle les opérations mathématiques suivantes sur le service : addition, soustraction, multiplication et division.</span><span class="sxs-lookup"><span data-stu-id="b40e1-105">The service is a calculator service and the COM client calls math operations—Add, Subtract, Multiply, and Divide—on the service.</span></span> <span data-ttu-id="b40e1-106">L'activité du client s'affiche dans les fenêtres de message.</span><span class="sxs-lookup"><span data-stu-id="b40e1-106">Client activity is visible in the message box windows.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b40e1-107">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="b40e1-107">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b40e1-108">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b40e1-108">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b40e1-109">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b40e1-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b40e1-110">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b40e1-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b40e1-111">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="b40e1-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\COM`  
  
 <span data-ttu-id="b40e1-112">Le service implémente un contrat `ICalculator` tel que défini dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="b40e1-112">The service implements an `ICalculator` contract defined as shown in the following code example.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="b40e1-113">L'exemple illustre les trois manières d'utiliser le moniker :</span><span class="sxs-lookup"><span data-stu-id="b40e1-113">The sample demonstrates the three alternative approaches for using the moniker:</span></span>  
  
- <span data-ttu-id="b40e1-114">Contrat typé : le contrat est enregistré sur l'ordinateur client sous la forme d'un type visible par COM.</span><span class="sxs-lookup"><span data-stu-id="b40e1-114">Typed contract – The contract is registered as a COM visible type on the client computer.</span></span>  
  
- <span data-ttu-id="b40e1-115">Contrat WSDL : le contrat est fourni sous la forme d'un document WSDL.</span><span class="sxs-lookup"><span data-stu-id="b40e1-115">WSDL contract – The contract is supplied in the form of a WSDL document.</span></span>  
  
- <span data-ttu-id="b40e1-116">Contrat MEX : le contrat est récupéré pendant l'exécution depuis un point de terminaison d'échange de métadonnées (Metadata Exchange, MEX).</span><span class="sxs-lookup"><span data-stu-id="b40e1-116">Metadata Exchange contract – The contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="typed-contract"></a><span data-ttu-id="b40e1-117">Contrat typé</span><span class="sxs-lookup"><span data-stu-id="b40e1-117">Typed Contract</span></span>  
 <span data-ttu-id="b40e1-118">Pour utiliser le moniker avec un contrat typé, les types attribués de manière appropriée au contrat de service doivent être enregistrés à l'aide de COM.</span><span class="sxs-lookup"><span data-stu-id="b40e1-118">To use the moniker with a typed contract use, appropriately attributed types for the service contract must be registered with COM.</span></span> <span data-ttu-id="b40e1-119">Tout d’abord, un client doit être généré à l’aide de l' [outil utilitaire de métadonnées ServiceModel (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b40e1-119">First, a client must be generated by using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="b40e1-120">Exécutez la commande suivante à partir d'une invite de commandes dans le répertoire client pour générer le proxy typé.</span><span class="sxs-lookup"><span data-stu-id="b40e1-120">Run the following command from a command prompt in the client directory to generate the typed proxy.</span></span>  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc /out:generatedClient.cs  
```  
  
 <span data-ttu-id="b40e1-121">Cette classe doit être intégrée à un projet, lequel doit être configuré pour générer un assembly visible par COM et signé lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="b40e1-121">This class must be included in a project and the project should be configured to generate a COM-visible, signed assembly when compiled.</span></span> <span data-ttu-id="b40e1-122">L'attribut suivant doit être intégré au fichier AssemblyInfo.cs :</span><span class="sxs-lookup"><span data-stu-id="b40e1-122">The following attribute should be included in the AssemblyInfo.cs file.</span></span>  
  
```csharp
[assembly: ComVisible(true)]  
```  
  
 <span data-ttu-id="b40e1-123">Une fois le projet généré, enregistrez les types visibles par COM en utilisant `regasm` tel qu'illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="b40e1-123">After building the project, register the COM-visible types by using `regasm` as shown in the following example.</span></span>  
  
```console  
regasm.exe /tlb:CalcProxy.tlb client.dll  
```  
  
 <span data-ttu-id="b40e1-124">L'assembly créé doit être ajouté au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="b40e1-124">The assembly that is created should be added to the Global Assembly Cache.</span></span> <span data-ttu-id="b40e1-125">Bien que cela ne soit pas strictement nécessaire, cela permet de localiser plus facilement l'assembly pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="b40e1-125">Though not strictly required, this simplifies the process of the runtime locating the assembly.</span></span> <span data-ttu-id="b40e1-126">La commande suivante ajoute l'assembly au Global Assembly Cache :</span><span class="sxs-lookup"><span data-stu-id="b40e1-126">The following command adds the assembly to the Global Assembly Cache.</span></span>  
  
```console  
gacutil.exe /i client.dll  
```  
  
> [!NOTE]
> <span data-ttu-id="b40e1-127">Le moniker de service requiert uniquement l'inscription de type et n'utilise pas le proxy pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-127">The service moniker requires only the type registration and does not use the proxy to communicate with the service.</span></span>  
  
 <span data-ttu-id="b40e1-128">L’application cliente ComCalcClient.vbs utilise la fonction `GetObject` et la syntaxe du moniker de service pour construire un proxy pour le service, notamment pour spécifier ses adresse, liaison et contrat.</span><span class="sxs-lookup"><span data-stu-id="b40e1-128">ComCalcClient.vbs client application uses the `GetObject` function to construct a proxy for the service, using the service moniker syntax to specify the address, binding, and contract for the service.</span></span>  
  
```vbscript
Set typedServiceMoniker = GetObject(  
"service4:address=http://localhost/ServiceModelSamples/service.svc, binding=wsHttpBinding,
contractType={9213C6D2-5A6F-3D26-839B-3BA9B82228D3}")  
```  
  
 <span data-ttu-id="b40e1-129">Les paramètres utilisés par le moniker spécifient :</span><span class="sxs-lookup"><span data-stu-id="b40e1-129">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="b40e1-130">Adresse du point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-130">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="b40e1-131">Liaison à utiliser par le client pour se connecter à ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b40e1-131">The binding that the client should use to connect with that endpoint.</span></span> <span data-ttu-id="b40e1-132">Dans ce cas, la liaison wsHttpBinding définie par le système est utilisée bien que des liaisons personnalisées puissent être définies dans les fichiers de configuration du client.</span><span class="sxs-lookup"><span data-stu-id="b40e1-132">In this case, the system-defined wsHttpBinding is used though custom bindings can be defined in client configuration files.</span></span> <span data-ttu-id="b40e1-133">Pour une utilisation avec Windows Script Host, les liaisons personnalisées sont définies dans un fichier Cscript.exe.config stocké dans le même répertoire que Cscript.exe.</span><span class="sxs-lookup"><span data-stu-id="b40e1-133">For use with the Windows Script Host, the custom binding is defined in a Cscript.exe.config file in the same directory as Cscript.exe.</span></span>  
  
- <span data-ttu-id="b40e1-134">Type du contrat pris en charge au niveau du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="b40e1-134">The type of the contract that is supported at the endpoint.</span></span> <span data-ttu-id="b40e1-135">Il s'agit du type généré et enregistré plus haut.</span><span class="sxs-lookup"><span data-stu-id="b40e1-135">This is the type that was generated and registered above.</span></span> <span data-ttu-id="b40e1-136">Étant donné que Visual Basic Script ne fournit pas d’environnement COM fortement typé, vous devez spécifier un identificateur pour le contrat.</span><span class="sxs-lookup"><span data-stu-id="b40e1-136">Because Visual Basic script does not provide a strongly typed COM environment, an identifier for the contract must be specified.</span></span> <span data-ttu-id="b40e1-137">Ce GUID correspond à l'identificateur `interfaceID` issu du CalcProxy.tlb. Il est peut être affiché à l'aide des outils COM tels que l'Explorateur d'objets d'OLE/COM (OleView.exe).</span><span class="sxs-lookup"><span data-stu-id="b40e1-137">This GUID is the `interfaceID` from CalcProxy.tlb, which can be viewed by using COM tools such as the OLE/COM Object Viewer (OleView.exe).</span></span> <span data-ttu-id="b40e1-138">Pour les environnements fortement typés, tels qu’Office VBA ou Visual Basic 6,0, l’ajout d’une référence explicite à la bibliothèque de types et la déclaration du type de l’objet proxy peuvent être utilisés à la place du paramètre de contrat.</span><span class="sxs-lookup"><span data-stu-id="b40e1-138">For strongly typed environments such as Office VBA or Visual Basic 6.0, adding an explicit reference to the type library and then declaring the type of the proxy object can be used in place of the contract parameter.</span></span> <span data-ttu-id="b40e1-139">Ceci permet également la prise en charge d'IntelliSense pendant le développement de l'application cliente.</span><span class="sxs-lookup"><span data-stu-id="b40e1-139">This also provides IntelliSense support during client application development.</span></span>  
  
 <span data-ttu-id="b40e1-140">Une fois l'instance de proxy générée à l'aide du moniker de service, l'application cliente peut appeler des méthodes sur ce proxy, ce qui provoque l'appel des opérations de service correspondantes de la part de l'infrastructure du moniker.</span><span class="sxs-lookup"><span data-stu-id="b40e1-140">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "Typed service moniker: 100 + 15.99 = " & typedServiceMoniker.Add(100, 15.99)  
```  
  
 Lorsque vous exécutez l'exemple, la réponse d'opération est affichée dans une fenêtre de message Windows Script Host. Cela démontre un client COM qui effectue des appels COM à l’aide du moniker typé pour communiquer avec un service WCF. <span data-ttu-id="b40e1-143">Bien que ce client utilise COM, les communications avec le service se composent uniquement d'appels de service Web.</span><span class="sxs-lookup"><span data-stu-id="b40e1-143">Despite the use of COM in the client application, the communication with the service consists only of Web service calls.</span></span>  
  
## <a name="wsdl-contract"></a><span data-ttu-id="b40e1-144">Contrat WSDL</span><span class="sxs-lookup"><span data-stu-id="b40e1-144">WSDL Contract</span></span>  
 <span data-ttu-id="b40e1-145">Pour utiliser le moniker à l'aide du contrat WSDL du service, aucune inscription de bibliothèque côté client n'est requise. Ce contrat doit cependant être récupéré via un mécanisme hors bande, par exemple à l'aide d'un navigateur permettant d'accéder au point de terminaison WSDL de ce service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-145">To use the moniker with a WSDL contract, no client library registration is required but the WSDL contract for the service must be retrieved through an out-of-band mechanism such as using a browser to access the WSDL endpoint for the service.</span></span> <span data-ttu-id="b40e1-146">Le moniker peut accéder ensuite à ce contrat pendant l'exécution.</span><span class="sxs-lookup"><span data-stu-id="b40e1-146">The moniker can then access that contract at execution time.</span></span>  
  
 <span data-ttu-id="b40e1-147">L'application cliente ComCalcClient.vbs utilise `FileSystemObject` pour accéder au fichier WSDL enregistré localement, puis utilise de nouveau la fonction `GetObject` pour construire un proxy de service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-147">The ComCalcClient.vbs client application uses the `FileSystemObject` to access the locally saved WSDL file and then again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Open the WSDL contract file and read it all into the wsdlContract string  
Const ForReading = 1  
Set objFSO = CreateObject("Scripting.FileSystemObject")  
Set objFile = objFSO.OpenTextFile("serviceWsdl.xml", ForReading)  
wsdlContract = objFile.ReadAll  
objFile.Close  
  
' Create a string for the service moniker including the content of the WSDL contract file  
wsdlMonikerString = "service4:address='http://localhost/ServiceModelSamples/service.svc'"  
wsdlMonikerString = wsdlMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
wsdlMonikerString = wsdlMonikerString + ", wsdl='" & wsdlContract & "'"  
wsdlMonikerString = wsdlMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set wsdlServiceMoniker = GetObject(wsdlMonikerString)  
```  
  
 <span data-ttu-id="b40e1-148">Les paramètres utilisés par le moniker spécifient :</span><span class="sxs-lookup"><span data-stu-id="b40e1-148">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="b40e1-149">Adresse du point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-149">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="b40e1-150">Liaison que le client doit utiliser pour se connecter à ce point de terminaison et l'espace de noms dans lequel cette liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="b40e1-150">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="b40e1-151">Dans ce cas, `wsHttpBinding_ICalculator` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b40e1-151">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="b40e1-152">WSDL qui définit le contrat.</span><span class="sxs-lookup"><span data-stu-id="b40e1-152">The WSDL that defines the contract.</span></span> <span data-ttu-id="b40e1-153">Dans ce cas, il s'agit de la chaîne lue à partir du fichier serviceWsdl.xml.</span><span class="sxs-lookup"><span data-stu-id="b40e1-153">In this case this is the string that has been read from the serviceWsdl.xml file.</span></span>  
  
- <span data-ttu-id="b40e1-154">Nom et espace de noms du contrat.</span><span class="sxs-lookup"><span data-stu-id="b40e1-154">The name and namespace of the contract.</span></span> <span data-ttu-id="b40e1-155">Cette identification est requise, le WSDL étant susceptible de contenir plusieurs contrats.</span><span class="sxs-lookup"><span data-stu-id="b40e1-155">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b40e1-156">Par défaut, les services WCF génèrent des fichiers WSDL distincts pour chaque espace de noms utilisé par.</span><span class="sxs-lookup"><span data-stu-id="b40e1-156">By default, WCF services generate separate WSDL files for each namespace that the use.</span></span> <span data-ttu-id="b40e1-157">Ces espaces sont liés à l'utilisation de la construction d'importation WSDL.</span><span class="sxs-lookup"><span data-stu-id="b40e1-157">These are linked with the use of the WSDL import construct.</span></span> <span data-ttu-id="b40e1-158">Le moniker escomptant une définition WSDL unique, le service doit utiliser un espace de noms unique comme illustré dans cet exemple ou les fichiers distincts doivent être fusionnés manuellement.</span><span class="sxs-lookup"><span data-stu-id="b40e1-158">Because the moniker expects a single WSDL definition, the service must either use a single namespace as demonstrated in this sample or the separate files must be manually merged.</span></span>  
  
 <span data-ttu-id="b40e1-159">Une fois l'instance de proxy générée à l'aide du moniker de service, l'application cliente peut appeler des méthodes sur ce proxy, ce qui provoque l'appel des opérations de service correspondantes de la part de l'infrastructure du moniker.</span><span class="sxs-lookup"><span data-stu-id="b40e1-159">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "WSDL service moniker: 145 - 76.54 = " & wsdlServiceMoniker.Subtract(145, 76.54)  
```  
  
 Lorsque vous exécutez l'exemple, la réponse d'opération est affichée dans une fenêtre de message Windows Script Host. <span data-ttu-id="b40e1-161">Cela démontre un client COM effectuant des appels COM à l’aide du moniker avec un contrat WSDL pour communiquer avec un service WCF.</span><span class="sxs-lookup"><span data-stu-id="b40e1-161">This demonstrates a COM client making COM calls using the moniker with a WSDL contract to communicate with a WCF service.</span></span>  
  
## <a name="metadata-exchange-contract"></a><span data-ttu-id="b40e1-162">Contrat d'échange de métadonnées</span><span class="sxs-lookup"><span data-stu-id="b40e1-162">Metadata Exchange Contract</span></span>  
 <span data-ttu-id="b40e1-163">Pour utiliser le moniker avec un contrat MEX, comme avec le contrat WSDL, aucune inscription côté client n'est requise.</span><span class="sxs-lookup"><span data-stu-id="b40e1-163">To use the moniker with a MEX contract, as with the WSDL contract, no client registration is required.</span></span> <span data-ttu-id="b40e1-164">Le contrat du service est récupéré pendant l'exécution via l'utilisation interne de l'échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="b40e1-164">The contract for the service is retrieved at execution time through the internal use of Metadata Exchange.</span></span>  
  
 <span data-ttu-id="b40e1-165">L'application cliente ComCalcClient.vbs utilise de nouveau la fonction `GetObject` pour construire un proxy de service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-165">The ComCalcClient.vbs client application again uses the `GetObject` function to construct a proxy for the service.</span></span>  
  
```vbscript  
' Create a string for the service moniker specifying the address to retrieve the service metadata from  
mexMonikerString = "service4:mexAddress='http://localhost/servicemodelsamples/service.svc/mex'"  
mexMonikerString = mexMonikerString + ", address='http://localhost/ServiceModelSamples/service.svc'"  
mexMonikerString = mexMonikerString + ", binding=WSHttpBinding_ICalculator, bindingNamespace='http://Microsoft.ServiceModel.Samples'"  
mexMonikerString = mexMonikerString + ", contract=ICalculator, contractNamespace='http://Microsoft.ServiceModel.Samples'"  
  
' Create the service moniker object  
Set mexServiceMoniker = GetObject(mexMonikerString)  
```  
  
 <span data-ttu-id="b40e1-166">Les paramètres utilisés par le moniker spécifient :</span><span class="sxs-lookup"><span data-stu-id="b40e1-166">The parameters used by the moniker specify:</span></span>  
  
- <span data-ttu-id="b40e1-167">Adresse du point de terminaison de l'échange de métadonnées du service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-167">The address of the service metadata exchange endpoint.</span></span>  
  
- <span data-ttu-id="b40e1-168">Adresse du point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-168">The address of the service endpoint.</span></span>  
  
- <span data-ttu-id="b40e1-169">Liaison que le client doit utiliser pour se connecter à ce point de terminaison et l'espace de noms dans lequel cette liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="b40e1-169">The binding that the client should use to connect with that endpoint and the namespace in which that binding is defined.</span></span> <span data-ttu-id="b40e1-170">Dans ce cas, `wsHttpBinding_ICalculator` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b40e1-170">In this case, the `wsHttpBinding_ICalculator` is used.</span></span>  
  
- <span data-ttu-id="b40e1-171">Nom et espace de noms du contrat.</span><span class="sxs-lookup"><span data-stu-id="b40e1-171">The name and namespace of the contract.</span></span> <span data-ttu-id="b40e1-172">Cette identification est requise, le WSDL étant susceptible de contenir plusieurs contrats.</span><span class="sxs-lookup"><span data-stu-id="b40e1-172">This identification is required because the WSDL may contain more than one contract.</span></span>  
  
 <span data-ttu-id="b40e1-173">Une fois l'instance de proxy générée à l'aide du moniker de service, l'application cliente peut appeler des méthodes sur ce proxy, ce qui provoque l'appel des opérations de service correspondantes de la part de l'infrastructure du moniker.</span><span class="sxs-lookup"><span data-stu-id="b40e1-173">Having constructed the proxy instance with the service moniker, the client application can call methods on the proxy, which results in the service moniker infrastructure calling the corresponding service operations.</span></span>  
  
```vbscript  
' Call the service operations using the moniker object  
WScript.Echo "MEX service moniker: 9 * 81.25 = " & mexServiceMoniker.Multiply(9, 81.25)  
```  
  
 Lorsque vous exécutez l'exemple, la réponse d'opération est affichée dans une fenêtre de message Windows Script Host. <span data-ttu-id="b40e1-175">Cela démontre un client COM effectuant des appels COM à l’aide du moniker avec un contrat MEX pour communiquer avec un service WCF.</span><span class="sxs-lookup"><span data-stu-id="b40e1-175">This demonstrates a COM client making COM calls using the moniker with a MEX contract to communicate with a WCF service.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="b40e1-176">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="b40e1-176">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="b40e1-177">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b40e1-177">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b40e1-178">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b40e1-178">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b40e1-179">À partir d’un Invite de commandes développeur pour Visual Studio, ouvrez le dossier \client\bin, sous le dossier propre à la langue.</span><span class="sxs-lookup"><span data-stu-id="b40e1-179">From a Developer Command Prompt for Visual Studio, open the \client\bin folder, under the language-specific folder.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="b40e1-180">Si vous utilisez Windows Vista, Windows Server 2008, Windows 7 ou Windows Server 2008 R2, assurez-vous d’exécuter l’invite de commandes avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b40e1-180">If you are using Windows Vista, Windows Server 2008, Windows 7, or Windows Server 2008 R2, make sure that you run the command prompt with administrator privileges.</span></span>  
  
4. <span data-ttu-id="b40e1-181">Tapez `tlbexp.exe client.dll /out:CalcProxy.tlb` pour exporter la dll dans un fichier TLB.</span><span class="sxs-lookup"><span data-stu-id="b40e1-181">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="b40e1-182">Un avertissement d'exportateur de bibliothèques de types est escompté mais ceci ne présente pas de problème dans la mesure où le type générique n'est pas requis.</span><span class="sxs-lookup"><span data-stu-id="b40e1-182">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
5. <span data-ttu-id="b40e1-183">Tapez `regasm.exe /tlb:CalcProxy.tlb client.dll` pour inscrire les types avec com.</span><span class="sxs-lookup"><span data-stu-id="b40e1-183">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="b40e1-184">Un avertissement d'exportateur de bibliothèques de types est escompté mais ceci ne présente pas de problème dans la mesure où le type générique n'est pas requis.</span><span class="sxs-lookup"><span data-stu-id="b40e1-184">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
6. <span data-ttu-id="b40e1-185">Tapez `gacutil.exe /i client.dll` pour ajouter l’assembly au global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="b40e1-185">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="b40e1-186">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="b40e1-186">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="b40e1-187">Vérifiez que vous pouvez accéder au service à l’aide d’un navigateur en tapant l’adresse suivante : `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="b40e1-187">Test that you can access the service using a browser by typing in the following address: `http://localhost/servicemodelsamples/service.svc`.</span></span> <span data-ttu-id="b40e1-188">Une page de confirmation doit s'afficher en réponse.</span><span class="sxs-lookup"><span data-stu-id="b40e1-188">A confirmation page should be displayed in response.</span></span>  
  
2. <span data-ttu-id="b40e1-189">Exécutez ComCalcClient.vbs à partir du dossier \client figurant dans le dossier correspondant à votre langue.</span><span class="sxs-lookup"><span data-stu-id="b40e1-189">Run ComCalcClient.vbs from \client, from under the language-specific folder.</span></span> <span data-ttu-id="b40e1-190">L'activité du client est affichée dans les fenêtres de message.</span><span class="sxs-lookup"><span data-stu-id="b40e1-190">Client activity is displayed in message box windows.</span></span>  
  
3. <span data-ttu-id="b40e1-191">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="b40e1-191">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="b40e1-192">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="b40e1-192">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="b40e1-193">Créez un répertoire virtuel nommé ServiceModelSamples sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-193">On the service computer, create a virtual directory named ServiceModelSamples.</span></span> <span data-ttu-id="b40e1-194">Le script Setupvroot.bat inclus dans l'exemple peut être utilisé pour créer le répertoire de disque et le répertoire virtuel.</span><span class="sxs-lookup"><span data-stu-id="b40e1-194">The Setupvroot.bat script included with the sample can be used to create the disk directory and virtual directory.</span></span>  
  
2. <span data-ttu-id="b40e1-195">Copiez les fichiers du programme de service depuis %SystemDrive%\Inetpub\wwwroot\servicemodelsamples vers le répertoire virtuel ServiceModelSamples.</span><span class="sxs-lookup"><span data-stu-id="b40e1-195">Copy the service program files from %SystemDrive%\Inetpub\wwwroot\servicemodelsamples to the ServiceModelSamples virtual directory on the service computer.</span></span> <span data-ttu-id="b40e1-196">Assurez-vous d'intégrer les fichiers au répertoire \bin.</span><span class="sxs-lookup"><span data-stu-id="b40e1-196">Be sure to include the files in the \bin directory.</span></span>  
  
3. <span data-ttu-id="b40e1-197">Copiez le fichier script du client depuis le dossier \client figurant dans le dossier correspondant à votre langue sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b40e1-197">Copy the client script file from the \client folder, under the language-specific folder, to the client computer.</span></span>  
  
4. <span data-ttu-id="b40e1-198">Dans le fichier script, modifiez l'adresse du point de terminaison en fonction de la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="b40e1-198">In the script file, change the address value of the endpoint definition to match the new address of your service.</span></span> <span data-ttu-id="b40e1-199">Remplacez toutes les occurrences de « localhost » de l'adresse par un nom de domaine complet.</span><span class="sxs-lookup"><span data-stu-id="b40e1-199">Replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
5. <span data-ttu-id="b40e1-200">Copiez le fichier WSDL sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b40e1-200">Copy the WSDL file to the client computer.</span></span> <span data-ttu-id="b40e1-201">Dans le fichier WSDL nommé serviceWsdl.xml, remplacez toutes les occurrences de localhost par le nom de domaine complet de votre serveur.</span><span class="sxs-lookup"><span data-stu-id="b40e1-201">In the WSDL file, serviceWsdl.xml, replace any references to "localhost" with a fully-qualified domain name in the address.</span></span>  
  
6. <span data-ttu-id="b40e1-202">Copiez la bibliothèque Client.dll depuis le dossier \client\bin figurant dans le dossier correspondant à votre langue dans un répertoire de l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b40e1-202">Copy the Client.dll library from the \client\bin folder, under the language-specific folder, to a directory on the client computer.</span></span>  
  
7. <span data-ttu-id="b40e1-203">À partir d'une invite de commandes, naviguez jusqu'à ce répertoire de destination.</span><span class="sxs-lookup"><span data-stu-id="b40e1-203">From a command prompt, navigate to that destination directory on the client computer.</span></span> <span data-ttu-id="b40e1-204">Si vous utilisez Windows Vista ou Windows Server 2008, veillez à exécuter l’invite de commandes en tant qu’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b40e1-204">If using Windows Vista or Windows Server 2008, make sure to run the command prompt as Administrator.</span></span>  
  
8. <span data-ttu-id="b40e1-205">Tapez `tlbexp.exe client.dll /out:CalcProxy.tlb` pour exporter la dll dans un fichier TLB.</span><span class="sxs-lookup"><span data-stu-id="b40e1-205">Type in `tlbexp.exe client.dll /out:CalcProxy.tlb` to export the dll to a tlb file.</span></span> <span data-ttu-id="b40e1-206">Un avertissement d'exportateur de bibliothèques de types est escompté mais ceci ne présente pas de problème dans la mesure où le type générique n'est pas requis.</span><span class="sxs-lookup"><span data-stu-id="b40e1-206">A "Type library exporter warning" is expected but is not an issue because the generic type is not required.</span></span>  
  
9. <span data-ttu-id="b40e1-207">Tapez `regasm.exe /tlb:CalcProxy.tlb client.dll` pour inscrire les types avec com.</span><span class="sxs-lookup"><span data-stu-id="b40e1-207">Type in `regasm.exe /tlb:CalcProxy.tlb client.dll` to register the types with COM.</span></span> <span data-ttu-id="b40e1-208">Assurez-vous que le chemin d’accès a été défini sur le dossier qui contient `regasm.exe` avant d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="b40e1-208">Ensure that path has been set to the folder that contains `regasm.exe` before you run the command.</span></span>  
  
10. <span data-ttu-id="b40e1-209">Tapez `gacutil.exe /i client.dll` pour ajouter l’assembly au global assembly cache.</span><span class="sxs-lookup"><span data-stu-id="b40e1-209">Type in `gacutil.exe /i client.dll` to add the assembly to the Global Assembly Cache.</span></span> <span data-ttu-id="b40e1-210">Assurez-vous que le chemin d’accès a été défini sur le dossier qui contient `gacutil.exe` avant d’exécuter la commande.</span><span class="sxs-lookup"><span data-stu-id="b40e1-210">Ensure that path has been set to the folder that contains `gacutil.exe` before you run the command.</span></span>  
  
11. <span data-ttu-id="b40e1-211">Assurez-vous que le service est accessible depuis l'ordinateur client à l'aide d'un navigateur.</span><span class="sxs-lookup"><span data-stu-id="b40e1-211">Test that you can access the service from the client computer using a browser.</span></span>  
  
12. <span data-ttu-id="b40e1-212">Sur l'ordinateur client, lancez ComCalcClient.vbs.</span><span class="sxs-lookup"><span data-stu-id="b40e1-212">On the client computer, launch ComCalcClient.vbs.</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="b40e1-213">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="b40e1-213">To clean up after the sample</span></span>  
  
- <span data-ttu-id="b40e1-214">Pour des raisons de sécurité, supprimez la définition du répertoire virtuel et les autorisations accordées pendant les étapes de l'installation, une fois l'exécution des exemples terminée.</span><span class="sxs-lookup"><span data-stu-id="b40e1-214">For security purposes, remove the virtual directory definition and permissions granted in the setup steps when you are finished with the samples.</span></span>
