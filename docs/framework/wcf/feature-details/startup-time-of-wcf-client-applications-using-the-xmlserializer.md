---
title: "Comment : améliorer le temps de démarrage des applications clientes WCF à l'aide de XmlSerializer"
ms.date: 03/30/2017
ms.assetid: 21093451-0bc3-4b1a-9a9d-05f7f71fa7d0
ms.openlocfilehash: 91712963908ecc56ff17fbac028389207544b82f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600255"
---
# <a name="how-to-improve-the-startup-time-of-wcf-client-applications-using-the-xmlserializer"></a><span data-ttu-id="2dd08-102">Comment : améliorer le temps de démarrage des applications clientes WCF à l'aide de XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="2dd08-102">How to: Improve the Startup Time of WCF Client Applications using the XmlSerializer</span></span>
<span data-ttu-id="2dd08-103">Les applications clientes et de services qui utilisent des types de données sérialisables à l'aide de <xref:System.Xml.Serialization.XmlSerializer> génèrent et compilent le code de sérialisation de ces types de données lors de l'exécution, ce qui peut provoquer des performances de démarrage lentes.</span><span class="sxs-lookup"><span data-stu-id="2dd08-103">Services and client applications that use data types that are serializable using the <xref:System.Xml.Serialization.XmlSerializer> generate and compile serialization code for those data types at runtime, which can result in slow start-up performance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2dd08-104">Le code de sérialisation prégénéré est réservé aux applications clientes, pas aux services.</span><span class="sxs-lookup"><span data-stu-id="2dd08-104">Pre-generated serialization code can only be used in client applications and not in services.</span></span>  
  
 <span data-ttu-id="2dd08-105">L' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) peut améliorer les performances de démarrage de ces applications en générant le code de sérialisation nécessaire à partir des assemblys compilés pour l’application.</span><span class="sxs-lookup"><span data-stu-id="2dd08-105">The [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) can improve start-up performance for these applications by generating the necessary serialization code from the compiled assemblies for the application.</span></span> <span data-ttu-id="2dd08-106">Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2dd08-106">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="2dd08-107">Les contrats de service et d'opération qui utilisent <xref:System.Xml.Serialization.XmlSerializer> sont marqués avec <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2dd08-107">Service and operation contracts that use the <xref:System.Xml.Serialization.XmlSerializer> are marked with the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code"></a><span data-ttu-id="2dd08-108">Pour générer du code de sérialisation XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="2dd08-108">To generate XmlSerializer serialization code</span></span>  
  
1. <span data-ttu-id="2dd08-109">Compilez votre code de service ou client dans un ou plusieurs assemblys.</span><span class="sxs-lookup"><span data-stu-id="2dd08-109">Compile your service or client code into one or more assemblies.</span></span>  
  
2. <span data-ttu-id="2dd08-110">Ouvrez une invite de commandes du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="2dd08-110">Open an SDK command prompt.</span></span>  
  
3. <span data-ttu-id="2dd08-111">À l'invite de commandes, lancez l'outil Svcutil.exe à l'aide du format suivant.</span><span class="sxs-lookup"><span data-stu-id="2dd08-111">At the command prompt, launch the Svcutil.exe tool using the following format.</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="2dd08-112">L'argument `assemblyPath` spécifie le chemin d'accès à un assembly contenant des types de contrat de service.</span><span class="sxs-lookup"><span data-stu-id="2dd08-112">The `assemblyPath` argument specifies the path to an assembly that contains service contract types.</span></span> <span data-ttu-id="2dd08-113">Svcutil.exe génère le code de sérialisation de tous les types de données utilisés dans les contrats de service de l'assembly d'application compilé qui peut être sérialisé à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="2dd08-113">Svcutil.exe generates serialization code for all data types used in service contracts in the compiled application assembly that can be serialized using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
     <span data-ttu-id="2dd08-114">Svcutil.exe peut uniquement générer du code de sérialisation C#.</span><span class="sxs-lookup"><span data-stu-id="2dd08-114">Svcutil.exe can only generate C# serialization code.</span></span> <span data-ttu-id="2dd08-115">Un fichier de code source est généré pour chaque assembly d'entrée.</span><span class="sxs-lookup"><span data-stu-id="2dd08-115">One source code file is generated for each input assembly.</span></span> <span data-ttu-id="2dd08-116">Vous ne pouvez pas utiliser le commutateur **/Language** pour modifier la langue du code généré.</span><span class="sxs-lookup"><span data-stu-id="2dd08-116">You cannot use the **/language** switch to change the language of the generated code.</span></span>  
  
     <span data-ttu-id="2dd08-117">Pour spécifier le chemin d’accès aux assemblys dépendants, utilisez l’option **/Reference** .</span><span class="sxs-lookup"><span data-stu-id="2dd08-117">To specify the path to dependent assemblies, use the **/reference** option.</span></span>  
  
4. <span data-ttu-id="2dd08-118">Rendez le code de sérialisation généré disponible pour votre application en utilisant l'une des options suivantes :</span><span class="sxs-lookup"><span data-stu-id="2dd08-118">Make the generated serialization code available to your application by using one of the following options:</span></span>  
  
    1. <span data-ttu-id="2dd08-119">Compilez le code de sérialisation généré dans un assembly séparé portant le nom [*assembly d’origine*]. Xmlserializers. dll (par exemple, MyApp. xmlserializers. dll).</span><span class="sxs-lookup"><span data-stu-id="2dd08-119">Compile the generated serialization code into a separate assembly with the name [*original assembly*].XmlSerializers.dll (for example, MyApp.XmlSerializers.dll).</span></span> <span data-ttu-id="2dd08-120">Votre application doit être en mesure de charger l'assembly, qui doit être signé avec la même clé que l'assembly d'origine.</span><span class="sxs-lookup"><span data-stu-id="2dd08-120">Your application must be able to load the assembly, which must be signed with the same key as the original assembly.</span></span> <span data-ttu-id="2dd08-121">Si vous recompilez l'assembly d'origine, vous devez régénérer l'assembly de sérialisation.</span><span class="sxs-lookup"><span data-stu-id="2dd08-121">If you recompile the original assembly, you must regenerate the serialization assembly.</span></span>  
  
    2. <span data-ttu-id="2dd08-122">Compilez le code de sérialisation généré dans un assembly distinct et utilisez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> sur le contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2dd08-122">Compile the generated serialization code into a separate assembly and use the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> on the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="2dd08-123">Définissez les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> pour pointer vers l'assembly de sérialisation compilé.</span><span class="sxs-lookup"><span data-stu-id="2dd08-123">Set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties to point to the compiled serialization assembly.</span></span>  
  
    3. <span data-ttu-id="2dd08-124">Compilez le code de sérialisation généré dans votre assembly d'application et ajoutez <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> au contrat de service qui utilise <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2dd08-124">Compile the generated serialization code into your application assembly and add the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute> to the service contract that uses the <xref:System.ServiceModel.XmlSerializerFormatAttribute>.</span></span> <span data-ttu-id="2dd08-125">Ne définissez pas les propriétés <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> ou <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="2dd08-125">Do not set the <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.AssemblyName%2A> or <xref:System.Xml.Serialization.XmlSerializerAssemblyAttribute.CodeBase%2A> properties.</span></span> <span data-ttu-id="2dd08-126">L'assembly de sérialisation par défaut est supposé être l'assembly actuel.</span><span class="sxs-lookup"><span data-stu-id="2dd08-126">The default serialization assembly is assumed to be the current assembly.</span></span>  
  
### <a name="to-generate-xmlserializer-serialization-code-in-visual-studio"></a><span data-ttu-id="2dd08-127">Pour générer le code de sérialisation XmlSerializer dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2dd08-127">To generate XmlSerializer serialization code in Visual Studio</span></span>  
  
1. <span data-ttu-id="2dd08-128">Créez le service WCF et les projets clients dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2dd08-128">Create the WCF service and client projects in Visual Studio.</span></span> <span data-ttu-id="2dd08-129">Ensuite, ajoutez une référence de service au projet client.</span><span class="sxs-lookup"><span data-stu-id="2dd08-129">Then, add a service reference to the client project.</span></span>  
  
2. <span data-ttu-id="2dd08-130">Ajoutez un <xref:System.ServiceModel.XmlSerializerFormatAttribute> au contrat de service dans le fichier *Reference.cs* dans le projet d’application cliente sous **serviceReference**  ->  **Reference. svcmap**.</span><span class="sxs-lookup"><span data-stu-id="2dd08-130">Add an <xref:System.ServiceModel.XmlSerializerFormatAttribute> to the service contract in the *reference.cs* file in the client app project under **serviceReference** -> **reference.svcmap**.</span></span> <span data-ttu-id="2dd08-131">Notez que vous devez afficher tous les fichiers dans **Explorateur de solutions** pour voir ces fichiers.</span><span class="sxs-lookup"><span data-stu-id="2dd08-131">Note that you need to show all files in **Solution Explorer** to see these files.</span></span>  
  
3. <span data-ttu-id="2dd08-132">Générez l’application cliente.</span><span class="sxs-lookup"><span data-stu-id="2dd08-132">Build the client app.</span></span>  
  
4. <span data-ttu-id="2dd08-133">Utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pour créer un fichier serializer *. cs* pré-généré à l’aide de la commande :</span><span class="sxs-lookup"><span data-stu-id="2dd08-133">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to create a pre-generated serializer *.cs* file by using the command:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer  <assemblyPath>*  
    ```  
  
     <span data-ttu-id="2dd08-134">L’argument assemblyPath spécifie le chemin d’accès à l’assembly du client WCF.</span><span class="sxs-lookup"><span data-stu-id="2dd08-134">The assemblyPath argument specifies the path to the WCF client assembly.</span></span>  
  
     <span data-ttu-id="2dd08-135">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="2dd08-135">Such as:</span></span>  
  
    ```console  
    svcutil.exe /t:xmlSerializer wcfclient.exe  
    ```  
  
     <span data-ttu-id="2dd08-136">Le fichier *WCFClient.xmlserializers.dll.cs* est généré.</span><span class="sxs-lookup"><span data-stu-id="2dd08-136">The *WCFClient.XmlSerializers.dll.cs* file will be generated.</span></span>  
  
5. <span data-ttu-id="2dd08-137">Compilez l’assembly de sérialisation préalablement généré.</span><span class="sxs-lookup"><span data-stu-id="2dd08-137">Compile the pre-generated serialization assembly.</span></span>  
  
     <span data-ttu-id="2dd08-138">En fonction de l’exemple de l’étape précédente, la commande compile est la suivante :</span><span class="sxs-lookup"><span data-stu-id="2dd08-138">Based on the example in the previous step, the compile command would be the following:</span></span>  
  
    ```console  
    csc /r:wcfclient.exe /out:WCFClient.XmlSerializers.dll /t:library WCFClient.XmlSerializers.dll.cs  
    ```  
  
     <span data-ttu-id="2dd08-139">Assurez-vous que le *fichier WCFClient. xmlserializers. dll* généré se trouve dans le même répertoire que l’application cliente, qui est *WCFClient. exe* dans ce cas.</span><span class="sxs-lookup"><span data-stu-id="2dd08-139">Make sure the generated *WCFClient.XmlSerializers.dll* is in the same directory as the client app, which is *WCFClient.exe* in this case.</span></span>  
  
6. <span data-ttu-id="2dd08-140">Exécutez l’application cliente comme d’habitude.</span><span class="sxs-lookup"><span data-stu-id="2dd08-140">Run the client app as usual.</span></span> <span data-ttu-id="2dd08-141">L’assembly de sérialisation prégénéré sera utilisé.</span><span class="sxs-lookup"><span data-stu-id="2dd08-141">The pre-generated serialization assembly will be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dd08-142">Exemple</span><span class="sxs-lookup"><span data-stu-id="2dd08-142">Example</span></span>  
 <span data-ttu-id="2dd08-143">La commande suivante génère des types de sérialisation pour les types `XmlSerializer` que les contrats de service de l'assembly utilisent.</span><span class="sxs-lookup"><span data-stu-id="2dd08-143">The following command generates serialization types for `XmlSerializer` types that any service contracts in the assembly use.</span></span>  
  
```console  
svcutil /t:xmlserializer myContractLibrary.exe  
```  
  
## <a name="see-also"></a><span data-ttu-id="2dd08-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dd08-144">See also</span></span>

- [<span data-ttu-id="2dd08-145">Outil Service Model Metadata Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="2dd08-145">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
