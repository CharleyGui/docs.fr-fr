---
title: 'Procédure : Utiliser EdmGen.exe pour générer le code de couche objet'
ms.date: 03/30/2017
ms.assetid: c44d2ebe-f66f-42cb-9741-4a3f0c2dcffb
ms.openlocfilehash: 9a73a803d310ebd847e49f4bd71609f8ef9f2944
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546638"
---
# <a name="how-to-use-edmgenexe-to-generate-object-layer-code"></a><span data-ttu-id="511a8-102">Procédure : Utiliser EdmGen.exe pour générer le code de couche objet</span><span class="sxs-lookup"><span data-stu-id="511a8-102">How to: Use EdmGen.exe to Generate Object-Layer Code</span></span>
<span data-ttu-id="511a8-103">Cette rubrique montre comment utiliser l’outil [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) pour générer le code de couche objet basé sur le fichier. csdl.</span><span class="sxs-lookup"><span data-stu-id="511a8-103">This topic shows how to use the [EDM Generator (EdmGen.exe)](edm-generator-edmgen-exe.md) tool to generate object-layer code  based on the .csdl file.</span></span>  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a><span data-ttu-id="511a8-104">Pour générer le code de couche objet pour le modèle School à l'aide d'EdmGen.exe dans le cadre d'un projet Visual Basic</span><span class="sxs-lookup"><span data-stu-id="511a8-104">To generate object-layer code for the School model for a Visual Basic project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="511a8-105">Créez la base de données School.</span><span class="sxs-lookup"><span data-stu-id="511a8-105">Create the School database.</span></span> <span data-ttu-id="511a8-106">Pour plus d’informations, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="511a8-106">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="511a8-107">Générez le modèle School ou obtenez le fichier School.csdl.</span><span class="sxs-lookup"><span data-stu-id="511a8-107">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="511a8-108">Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="511a8-108">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="511a8-109">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="511a8-109">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.vb /language:VB  
    ```  
  
### <a name="to-generate-object-layer-code-for-the-school-model-for-a-c-project-using-edmgenexe"></a><span data-ttu-id="511a8-110">Pour générer le code de couche objet pour le modèle School à l'aide d'EdmGen.exe dans le cadre d'un projet C#</span><span class="sxs-lookup"><span data-stu-id="511a8-110">To generate object-layer code for the School model for a C# project using EdmGen.exe</span></span>  
  
1. <span data-ttu-id="511a8-111">Créez la base de données School.</span><span class="sxs-lookup"><span data-stu-id="511a8-111">Create the School database.</span></span> <span data-ttu-id="511a8-112">Pour plus d’informations, consultez [création de l’exemple de base de données School](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="511a8-112">For more information, see [Creating the School Sample Database](/previous-versions/dotnet/netframework-4.0/bb399731(v=vs.100)).</span></span>  
  
2. <span data-ttu-id="511a8-113">Générez le modèle School ou obtenez le fichier School.csdl.</span><span class="sxs-lookup"><span data-stu-id="511a8-113">Generate the School model or obtain the School.csdl file.</span></span> <span data-ttu-id="511a8-114">Pour plus d’informations, consultez [Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="511a8-114">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>  
  
3. <span data-ttu-id="511a8-115">À l'invite de commandes, exécutez la commande suivante sans saut de ligne :</span><span class="sxs-lookup"><span data-stu-id="511a8-115">At the command prompt, execute the following command without line breaks:</span></span>  
  
    ```console  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:EntityClassGeneration
    /incsdl:.\School.csdl /outobjectlayer:.\School.Objects.cs /language:CSharp  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="511a8-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="511a8-116">See also</span></span>

- [<span data-ttu-id="511a8-117">Modélisation et mappage</span><span class="sxs-lookup"><span data-stu-id="511a8-117">Modeling and Mapping</span></span>](modeling-and-mapping.md)
- <span data-ttu-id="511a8-118">[Comment : configurer manuellement un projet Entity Framework](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="511a8-118">[How to: Manually Configure an Entity Framework Project](/previous-versions/dotnet/netframework-4.0/bb738546(v=vs.100))</span></span>
- <span data-ttu-id="511a8-119">[Outils ADO.NET Entity Data Model](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="511a8-119">[ADO.NET Entity Data Model  Tools](/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
- <span data-ttu-id="511a8-120">[Comment : prégénérer les vues pour améliorer les performances des requêtes](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="511a8-120">[How to: Pre-Generate Views to Improve Query Performance](/previous-versions/dotnet/netframework-4.0/bb896240(v=vs.100))</span></span>
- [<span data-ttu-id="511a8-121">Procédure : Utiliser EdmGen.exe pour générer des fichiers de modèle et des fichiers de mappage</span><span class="sxs-lookup"><span data-stu-id="511a8-121">How to: Use EdmGen.exe to Generate the Model and Mapping Files</span></span>](how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)
