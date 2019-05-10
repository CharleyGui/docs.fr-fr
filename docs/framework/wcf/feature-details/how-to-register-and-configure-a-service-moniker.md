---
title: 'Procédure : inscrire et configurer un moniker de service'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], configure service monikers
- COM [WCF], register service monikers
ms.assetid: e5e16c80-8a8e-4eef-af53-564933b651ef
ms.openlocfilehash: f1f2b462ef0412b0f11a9ba5074f7546e6ee84f2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64643763"
---
# <a name="how-to-register-and-configure-a-service-moniker"></a><span data-ttu-id="d39f1-102">Procédure : inscrire et configurer un moniker de service</span><span class="sxs-lookup"><span data-stu-id="d39f1-102">How to: Register and Configure a Service Moniker</span></span>
<span data-ttu-id="d39f1-103">Avant d’utiliser le moniker de service Windows Communication Foundation (WCF) dans une application COM avec un contrat typé, vous devez inscrire les types attribués requis avec COM et configurer l’application COM et le moniker avec la liaison requise configuration.</span><span class="sxs-lookup"><span data-stu-id="d39f1-103">Before using the Windows Communication Foundation (WCF) service moniker within a COM application with a typed contract, you must register the required attributed types with COM, and configure the COM application and the moniker with the required binding configuration.</span></span>  
  
### <a name="to-register-the-required-attributed-types-with-com"></a><span data-ttu-id="d39f1-104">Pour inscrire les types avec attributs requis avec COM</span><span class="sxs-lookup"><span data-stu-id="d39f1-104">To register the required attributed types with COM</span></span>  
  
1. <span data-ttu-id="d39f1-105">Utilisez le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) outil pour récupérer le contrat de métadonnées à partir du service WCF.</span><span class="sxs-lookup"><span data-stu-id="d39f1-105">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool to retrieve the metadata contract from the WCF service.</span></span> <span data-ttu-id="d39f1-106">Cela génère le code source pour un assembly de client WCF et un fichier de configuration d’application cliente.</span><span class="sxs-lookup"><span data-stu-id="d39f1-106">This generates the source code for a WCF client assembly and a client application configuration file.</span></span>  
  
2. <span data-ttu-id="d39f1-107">Vérifiez que les types dans l'assembly sont marqués comme `ComVisible`.</span><span class="sxs-lookup"><span data-stu-id="d39f1-107">Ensure that the types in the assembly are marked as `ComVisible`.</span></span> <span data-ttu-id="d39f1-108">Pour cela, ajoutez l'attribut suivant au fichier AssemblyInfo.cs dans votre projet Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d39f1-108">To do so, add the following attribute to the AssemblyInfo.cs file in your Visual Studio project.</span></span>  
  
    ```  
    [assembly: ComVisible(true)]  
    ```  
  
3. <span data-ttu-id="d39f1-109">Compilez le client WCF géré comme un assembly avec nom fort.</span><span class="sxs-lookup"><span data-stu-id="d39f1-109">Compile the managed WCF client as a strong-named assembly.</span></span> <span data-ttu-id="d39f1-110">Cette procédure requiert une signature à l'aide d'une paire de clés de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="d39f1-110">This requires signing with a cryptographic key pair.</span></span> <span data-ttu-id="d39f1-111">Pour plus d’informations, consultez [signature d’un Assembly avec un nom fort](https://go.microsoft.com/fwlink/?LinkId=94874) dans le Guide du développeur de .NET.</span><span class="sxs-lookup"><span data-stu-id="d39f1-111">For more information, see [Signing an Assembly with a Strong Name](https://go.microsoft.com/fwlink/?LinkId=94874) in the .NET Developer's Guide.</span></span>  
  
4. <span data-ttu-id="d39f1-112">Utilisez l'outil Assembly Registration Tool (Regasm.exe) avec l'option `/tlb` pour inscrire les types dans l'assembly avec COM.</span><span class="sxs-lookup"><span data-stu-id="d39f1-112">Use the Assembly Registration (Regasm.exe) tool with the `/tlb` option to register the types in the assembly with COM.</span></span>  
  
5. <span data-ttu-id="d39f1-113">Utilisez l'outil Global Assembly Cache Tool (Gacutil.exe) pour ajouter l'assembly au Global Assembly Cache.</span><span class="sxs-lookup"><span data-stu-id="d39f1-113">Use the Global Assembly Cache (Gacutil.exe) tool to add the assembly to the global assembly cache.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d39f1-114">La signature de l'assembly et son ajout au Global Assembly Cache sont deux étapes facultatives, mais elles peuvent simplifier le processus de chargement de l'assembly à partir de l'emplacement approprié au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="d39f1-114">Signing the assembly and adding it to the Global Assembly Cache are optional steps, but they can simplify the process of loading the assembly from the correct location at runtime.</span></span>  
  
### <a name="to-configure-the-com-application-and-the-moniker-with-the-required-binding-configuration"></a><span data-ttu-id="d39f1-115">Pour configurer l’application COM et le moniker à l’aide des paramètres de liaison requis</span><span class="sxs-lookup"><span data-stu-id="d39f1-115">To configure the COM application and the moniker with the required binding configuration</span></span>  
  
- <span data-ttu-id="d39f1-116">Placez les définitions de liaison (générées par le [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) dans le fichier de configuration d’application client généré) dans le fichier de configuration de l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="d39f1-116">Place the binding definitions (generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) in the generated client application configuration file) in the client application's configuration file.</span></span> <span data-ttu-id="d39f1-117">Par exemple, pour un fichier exécutable Visual Basic 6.0 nommé CallCenterClient.exe, la configuration doit être placée dans un fichier nommé CallCenterConfig.exe.config, dans le même répertoire que le fichier exécutable.</span><span class="sxs-lookup"><span data-stu-id="d39f1-117">For example, for a Visual Basic 6.0 executable named CallCenterClient.exe, the configuration should be placed in a file named CallCenterConfig.exe.config within the same directory as the executable.</span></span> <span data-ttu-id="d39f1-118">L'application cliente peut maintenant utiliser le moniker.</span><span class="sxs-lookup"><span data-stu-id="d39f1-118">The client application can now use the moniker.</span></span> <span data-ttu-id="d39f1-119">Notez que la configuration de liaison n’est pas requise si l’un des types fournis par WCF de liaison standard.</span><span class="sxs-lookup"><span data-stu-id="d39f1-119">Note that the binding configuration is not required if using one of the standard binding types provided by WCF.</span></span>  
  
     <span data-ttu-id="d39f1-120">Le type suivant est inscrit.</span><span class="sxs-lookup"><span data-stu-id="d39f1-120">The following type is registered.</span></span>  
  
    ```  
    using System.ServiceModel;  
  
    ...  
  
    [ServiceContract]   
    public interface IMathService   
    {  
    [OperationContract]  
    public int Add(int x, int y);  
    [OperationContract]  
    public int Subtract(int x, int y);  
    }  
    ```  
  
     <span data-ttu-id="d39f1-121">L’application est exposée à l’aide d’une liaison `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="d39f1-121">The application is exposed using a `wsHttpBinding` binding.</span></span> <span data-ttu-id="d39f1-122">Pour une configuration de type et d'application donnée, les exemples de chaînes de moniker suivants sont utilisés.</span><span class="sxs-lookup"><span data-stu-id="d39f1-122">For the given type and application configuration, the following example moniker strings are used.</span></span>  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1  
    ```  
  
     `or`  
  
    ```  
    service4:address=http://localhost/MathService, binding=wsHttpBinding, bindingConfiguration=Binding1, contract={36ADAD5A-A944-4d5c-9B7C-967E4F00A090}  
    ```  
  
     <span data-ttu-id="d39f1-123">Vous pouvez utiliser l'une ou l'autre de ces chaînes de moniker à partir de l'application Visual Basic 6.0, après avoir ajouté une référence à l'assembly qui contient les types `IMathService`, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="d39f1-123">You can use either of these moniker strings from within a Visual Basic 6.0 application, after adding a reference to the assembly that contains the `IMathService` types, as shown in the following sample code.</span></span>  
  
    ```  
    Dim MathProxy As IMathService  
    Dim result As Integer  
  
    Set MathProxy = GetObject( _  
            "service4:address=http://localhost/MathService, _  
            binding=wsHttpBinding, _  
            bindingConfiguration=Binding1")  
  
    result = MathProxy.Add(3, 5)  
    ```  
  
     <span data-ttu-id="d39f1-124">Dans cet exemple, la définition de la configuration de liaison `Binding1` est stockée dans un fichier de configuration judicieusement nommé pour l’application cliente, par exemple vb6nomapp.exe.config.</span><span class="sxs-lookup"><span data-stu-id="d39f1-124">In this example, the definition for the binding configuration `Binding1` is stored in a suitably named configuration file for the client application, such as vb6appname.exe.config.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d39f1-125">Vous pouvez utiliser un code semblable dans une application C#, C++ ou d'un autre langage .NET.</span><span class="sxs-lookup"><span data-stu-id="d39f1-125">You can use similar code in a C#, a C++, or any other .NET Language application.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d39f1-126">: Si le moniker est incorrect ou si le service est indisponible, l’appel à `GetObject` renvoie une erreur de « Syntaxe non valide ».</span><span class="sxs-lookup"><span data-stu-id="d39f1-126">: If the moniker is malformed or if the service is unavailable, the call to `GetObject` returns an error of "Invalid Syntax".</span></span> <span data-ttu-id="d39f1-127">Si vous recevez cette erreur, assurez-vous que le moniker que vous utilisez est correct et que le service est disponible.</span><span class="sxs-lookup"><span data-stu-id="d39f1-127">If you receive this error, make sure the moniker you are using is correct and the service is available.</span></span>  
  
     <span data-ttu-id="d39f1-128">Bien que cette rubrique porte sur l'utilisation du moniker de service à partir du code VB 6.0, vous pouvez utiliser un moniker de service à partir d'autres langages.</span><span class="sxs-lookup"><span data-stu-id="d39f1-128">Although this topic focuses on using the service moniker from VB 6.0 code, you can use a service moniker from other languages.</span></span> <span data-ttu-id="d39f1-129">Lors de l'utilisation d'un moniker à partir du code C++, l'assembly généré par Svcutil.exe doit être importé avec le paramètre « no_namespace named_guids raw_interfaces_only », tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="d39f1-129">When using a moniker from C++ code the Svcutil.exe generated assembly should be imported with "no_namespace named_guids raw_interfaces_only" as shown in the following code.</span></span>  
  
    ```  
    #import "ComTestProxy.tlb" no_namespace named_guids  
    ```  
  
     <span data-ttu-id="d39f1-130">Cela modifie les définitions d'interface importées afin que toutes les méthodes retournent un `HResult`.</span><span class="sxs-lookup"><span data-stu-id="d39f1-130">This modifies the imported interface definitions so that all methods return an `HResult`.</span></span> <span data-ttu-id="d39f1-131">Toutes les autres valeurs de retour sont converties en paramètres de sortie.</span><span class="sxs-lookup"><span data-stu-id="d39f1-131">Any other return values are converted into out parameters.</span></span> <span data-ttu-id="d39f1-132">L'exécution globale des méthodes reste la même.</span><span class="sxs-lookup"><span data-stu-id="d39f1-132">The overall execution of the methods remains the same.</span></span> <span data-ttu-id="d39f1-133">Cela vous permet de déterminer la cause d'une exception lorsque vous appelez une méthode sur le proxy.</span><span class="sxs-lookup"><span data-stu-id="d39f1-133">This allows you to determine the cause of an exception when calling a method on the proxy.</span></span> <span data-ttu-id="d39f1-134">Cette fonctionnalité n'est disponible qu'à partir du code C++.</span><span class="sxs-lookup"><span data-stu-id="d39f1-134">This functionality is only available from C++ code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d39f1-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d39f1-135">See also</span></span>

- [<span data-ttu-id="d39f1-136">Outil ServiceModel Metadata Utility (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="d39f1-136">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
