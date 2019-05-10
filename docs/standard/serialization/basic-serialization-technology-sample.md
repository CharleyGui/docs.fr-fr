---
title: Sérialisation de base, exemple de technologie
ms.date: 03/30/2017
ms.assetid: 9d824e16-08d1-4a36-bc7f-2388c1f75f34
ms.openlocfilehash: 860a33adcb2109ac26045b37631ede37fe1be362
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602480"
---
# <a name="basic-serialization-technology-sample"></a><span data-ttu-id="abf5d-102">Sérialisation de base, exemple de technologie</span><span class="sxs-lookup"><span data-stu-id="abf5d-102">Basic Serialization Technology Sample</span></span>
[<span data-ttu-id="abf5d-103">Télécharger l’exemple</span><span class="sxs-lookup"><span data-stu-id="abf5d-103">Download sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Runtime%20Serialization/Basic.zip.exe)  
  
 <span data-ttu-id="abf5d-104">Cet exemple montre la capacité du Common Language Runtime à sérialiser un graphique d'objets en mémoire dans un flux.</span><span class="sxs-lookup"><span data-stu-id="abf5d-104">This sample demonstrates the common language runtime's ability to serialize an object graph in memory to a stream.</span></span> <span data-ttu-id="abf5d-105">Cet exemple peut utiliser <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> pour la sérialisation.</span><span class="sxs-lookup"><span data-stu-id="abf5d-105">This sample can use either the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> or the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> for serialization.</span></span> <span data-ttu-id="abf5d-106">Une liste liée, remplie de données, est sérialisée ou désérialisée dans un flux de fichiers ou à partir de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="abf5d-106">A linked list, filled with data, is serialized or deserialized to or from a file stream.</span></span> <span data-ttu-id="abf5d-107">Dans les deux cas, la liste est affichée afin que vous puissiez consulter les résultats.</span><span class="sxs-lookup"><span data-stu-id="abf5d-107">In either case the list is displayed so that you can see the results.</span></span> <span data-ttu-id="abf5d-108">Il s'agit d'une liste liée de type `LinkedList`, un type défini par cet exemple.</span><span class="sxs-lookup"><span data-stu-id="abf5d-108">The linked list is of type `LinkedList`, a type defined by this sample.</span></span>  
  
 <span data-ttu-id="abf5d-109">Pour plus d'informations sur la sérialisation, consultez les commentaires inclus dans les fichiers de code source et dans les fichiers build-proj.</span><span class="sxs-lookup"><span data-stu-id="abf5d-109">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="abf5d-110">Pour générer l'exemple à partir de l'invite de commandes</span><span class="sxs-lookup"><span data-stu-id="abf5d-110">To build the sample using the Command Prompt</span></span>  
  
1. <span data-ttu-id="abf5d-111">Accédez à l'un des sous-répertoires spécifiques aux différents langages dans le répertoire Technologies\Serialization\Runtime Serialization\Basic, à l'aide de l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="abf5d-111">Navigate to one of the language-specific subdirectories under the Technologies\Serialization\Runtime Serialization\Basic directory, using the command prompt.</span></span>  
  
2. <span data-ttu-id="abf5d-112">Tapez **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** ou **msbuild SerializationVB.sln** sur la ligne de commande, selon votre choix de langage de programmation.</span><span class="sxs-lookup"><span data-stu-id="abf5d-112">Type **msbuild SerializationCS.sln**, **msbuild SerializationJSL.sln** or **msbuild SerializationVB.sln**, depending on your choice of programming language, at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="abf5d-113">Pour générer l'exemple à l'aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="abf5d-113">To build the sample using Visual Studio</span></span>  
  
1. <span data-ttu-id="abf5d-114">Ouvrez l'[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] et accédez à l'un des sous-répertoires spécifiques aux différents langages de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="abf5d-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2. <span data-ttu-id="abf5d-115">Double-cliquez sur l'icône du fichier SerializationCS.sln, SerializationJSL.sln ou SerializationVB.sln, selon votre choix de langage de programmation, pour ouvrir le fichier dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="abf5d-115">Double-click the icon for the SerializationCS.sln, SerializationJSL.sln or SerializationVB.sln file, depending on your choice of programming language, to open the file in Visual Studio.</span></span>  
  
3. <span data-ttu-id="abf5d-116">Dans le menu **Générer**, sélectionnez **Générer la solution**.</span><span class="sxs-lookup"><span data-stu-id="abf5d-116">In the **Build** menu, select **Build Solution**.</span></span>  
  
 <span data-ttu-id="abf5d-117">L'exemple d'application est généré dans le sous-répertoire \bin ou \bin\Debug par défaut.</span><span class="sxs-lookup"><span data-stu-id="abf5d-117">The sample application will be built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="abf5d-118">Pour exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="abf5d-118">To run the sample</span></span>  
  
1. <span data-ttu-id="abf5d-119">Accédez au répertoire qui contient le fichier exécutable créé.</span><span class="sxs-lookup"><span data-stu-id="abf5d-119">Navigate to the directory containing the built executable.</span></span>  
  
2. <span data-ttu-id="abf5d-120">Tapez **Serialization.exe**, ainsi que les valeurs de paramètres souhaitées, sur la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="abf5d-120">Type **Serialization.exe**, along with the parameter values you desire, at the command line.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="abf5d-121">Cet exemple génère une application console.</span><span class="sxs-lookup"><span data-stu-id="abf5d-121">This sample builds a console application.</span></span> <span data-ttu-id="abf5d-122">Vous devez la lancer à l'aide de l'invite de commandes pour pouvoir afficher sa sortie.</span><span class="sxs-lookup"><span data-stu-id="abf5d-122">You must launch it using the command prompt in order to view its output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abf5d-123">Notes</span><span class="sxs-lookup"><span data-stu-id="abf5d-123">Remarks</span></span>  
 <span data-ttu-id="abf5d-124">L'exemple d'application accepte des paramètres de ligne de commande indiquant le test à exécuter.</span><span class="sxs-lookup"><span data-stu-id="abf5d-124">The sample application accepts command line parameters indicating which test you would like to execute.</span></span> <span data-ttu-id="abf5d-125">Pour sérialiser une liste de 10 nœuds dans un fichier nommé **Test.xml** à l’aide du formateur SOAP, utilisez les paramètres **sx Test.xml 10**.</span><span class="sxs-lookup"><span data-stu-id="abf5d-125">To serialize a 10-node list to a file named **Test.xml** using the SOAP formatter, use the parameters **sx Test.xml 10**.</span></span>  
  
 <span data-ttu-id="abf5d-126">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="abf5d-126">For Example:</span></span>  
  
 <span data-ttu-id="abf5d-127">**Serialize.exe -sx Test.xml 10**</span><span class="sxs-lookup"><span data-stu-id="abf5d-127">**Serialize.exe -sx Test.xml 10**</span></span>  
  
 <span data-ttu-id="abf5d-128">Pour désérialiser le fichier **Test.xml** de l’exemple précédent, utilisez les paramètres **dx Test.xml**.</span><span class="sxs-lookup"><span data-stu-id="abf5d-128">To deserialize the **Test.xml** file from the previous example, use the parameters **dx Test.xml**.</span></span>  
  
 <span data-ttu-id="abf5d-129">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="abf5d-129">For Example:</span></span>  
  
 <span data-ttu-id="abf5d-130">**Serialize.exe -dx Test.xml**</span><span class="sxs-lookup"><span data-stu-id="abf5d-130">**Serialize.exe -dx Test.xml**</span></span>  
  
 <span data-ttu-id="abf5d-131">Dans les deux exemples précités, la lettre "x" dans le commutateur de ligne de commande indique que vous souhaitez effectuer une sérialisation SOAP XML.</span><span class="sxs-lookup"><span data-stu-id="abf5d-131">In the two examples above, the "x" in the command line switch indicates that you want XML SOAP serialization.</span></span> <span data-ttu-id="abf5d-132">Vous pouvez utiliser à la place la lettre "b" pour effectuer une sérialisation binaire.</span><span class="sxs-lookup"><span data-stu-id="abf5d-132">You can use "b" in its place to use binary serialization.</span></span> <span data-ttu-id="abf5d-133">Si vous souhaitez effectuer une sérialisation avec un très grand nombre de nœuds, il peut être intéressant de rediriger la sortie de console vers un fichier.</span><span class="sxs-lookup"><span data-stu-id="abf5d-133">If you wish to try serialization with a very large number of nodes, you might want to redirect the console output to a file.</span></span>  
  
 <span data-ttu-id="abf5d-134">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="abf5d-134">For Example:</span></span>  
  
 <span data-ttu-id="abf5d-135">**Serialize.exe -sb Test.bin 10000 >fichier_quelconque.txt**</span><span class="sxs-lookup"><span data-stu-id="abf5d-135">**Serialize.exe -sb Test.bin 10000 >somefile.txt**</span></span>  
  
 <span data-ttu-id="abf5d-136">Les éléments de la liste suivante décrivent brièvement les classes et les technologies utilisées par cet exemple.</span><span class="sxs-lookup"><span data-stu-id="abf5d-136">The following bullets briefly describe the classes and technologies used by this sample.</span></span>  
  
- <span data-ttu-id="abf5d-137">Sérialisation du runtime</span><span class="sxs-lookup"><span data-stu-id="abf5d-137">Runtime Serialization</span></span>  
  
    - <span data-ttu-id="abf5d-138"><xref:System.Runtime.Serialization.IFormatter> Utilisé pour référencer un <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ou un <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> objet.</span><span class="sxs-lookup"><span data-stu-id="abf5d-138"><xref:System.Runtime.Serialization.IFormatter> Used to refer to either a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> or a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> object.</span></span>  
  
    - <span data-ttu-id="abf5d-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Utilisé pour sérialiser une liste liée à un flux de données dans un format binaire.</span><span class="sxs-lookup"><span data-stu-id="abf5d-139"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> Used to serialize a linked list to a stream in a binary format.</span></span> <span data-ttu-id="abf5d-140">Le formateur binaire utilise un format reconnu uniquement par le type <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="abf5d-140">The binary formatter uses a format that only the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> type understands.</span></span> <span data-ttu-id="abf5d-141">Toutefois, les données sont concises.</span><span class="sxs-lookup"><span data-stu-id="abf5d-141">However, the data is concise.</span></span>  
  
    - <span data-ttu-id="abf5d-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Utilisé pour sérialiser une liste liée à un flux au format SOAP.</span><span class="sxs-lookup"><span data-stu-id="abf5d-142"><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> Used to serialize a linked list to a stream in the SOAP format.</span></span> <span data-ttu-id="abf5d-143">SOAP est un format standard.</span><span class="sxs-lookup"><span data-stu-id="abf5d-143">SOAP is a standard format.</span></span>  
  
- <span data-ttu-id="abf5d-144">E/S de flux</span><span class="sxs-lookup"><span data-stu-id="abf5d-144">Stream I/O</span></span>  
  
    - <span data-ttu-id="abf5d-145"><xref:System.IO.Stream> Utilisé pour effectuer la sérialisation et la désérialisation.</span><span class="sxs-lookup"><span data-stu-id="abf5d-145"><xref:System.IO.Stream> Used to serialize and deserialize.</span></span> <span data-ttu-id="abf5d-146">Le flux spécifique utilisé dans cet exemple est de type <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="abf5d-146">The specific stream type used in this sample is the <xref:System.IO.FileStream> type.</span></span> <span data-ttu-id="abf5d-147">Toutefois, la sérialisation peut être utilisée avec n'importe quel type dérivé de <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="abf5d-147">However, serialization can be used with any type derived from <xref:System.IO.Stream>.</span></span>  
  
    - <span data-ttu-id="abf5d-148"><xref:System.IO.File> Utilisé pour créer des objets <xref:System.IO.FileStream> afin de lire et de créer des fichiers sur le disque.</span><span class="sxs-lookup"><span data-stu-id="abf5d-148"><xref:System.IO.File> Used to create <xref:System.IO.FileStream> objects for reading and creating files on disk.</span></span>  
  
    - <span data-ttu-id="abf5d-149"><xref:System.IO.FileStream> Utilisé pour sérialiser et désérialiser des listes liées.</span><span class="sxs-lookup"><span data-stu-id="abf5d-149"><xref:System.IO.FileStream> Used to serialize and deserialize linked lists.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abf5d-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="abf5d-150">See also</span></span>

- <xref:System.IO>
- <xref:System.IO.File>
- <xref:System.IO.FileStream>
- <xref:System.IO.Stream>
- <xref:System.Random>
- <xref:System.Runtime.Serialization>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.IFormatter>
- <xref:System.SerializableAttribute>
- <xref:System.Xml.Serialization>
- [<span data-ttu-id="abf5d-151">Sérialisation de base</span><span class="sxs-lookup"><span data-stu-id="abf5d-151">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)
- [<span data-ttu-id="abf5d-152">Sérialisation binaire</span><span class="sxs-lookup"><span data-stu-id="abf5d-152">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)
- [<span data-ttu-id="abf5d-153">Contrôle de la sérialisation XML à l’aide d’attributs</span><span class="sxs-lookup"><span data-stu-id="abf5d-153">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)
- [<span data-ttu-id="abf5d-154">Introduction à la sérialisation XML</span><span class="sxs-lookup"><span data-stu-id="abf5d-154">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)
- [<span data-ttu-id="abf5d-155">Sérialisation</span><span class="sxs-lookup"><span data-stu-id="abf5d-155">Serialization</span></span>](../../../docs/standard/serialization/index.md)
- [<span data-ttu-id="abf5d-156">Sérialisation XML et SOAP</span><span class="sxs-lookup"><span data-stu-id="abf5d-156">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
