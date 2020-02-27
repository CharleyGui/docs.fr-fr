---
title: Fichiers mappés en mémoire
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: 7d80099fcfcba58cd863004ba7faf0bafa3abd09
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628018"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="85f16-102">Fichiers mappés en mémoire</span><span class="sxs-lookup"><span data-stu-id="85f16-102">Memory-Mapped Files</span></span>
<span data-ttu-id="85f16-103">Un fichier mappé en mémoire comporte le contenu d'un fichier en mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="85f16-103">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="85f16-104">Ce mappage entre un fichier et un espace mémoire permet à une application incluant plusieurs processus de modifier le fichier en lisant et en écrivant directement dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-104">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="85f16-105">À compter de .NET Framework 4, vous pouvez utiliser du code managé pour accéder aux fichiers mappés en mémoire de la même façon que les fonctions Windows natives accèdent à des fichiers mappés en mémoire, comme décrit dans [Gestion des fichiers mappés en mémoire](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="85f16-105">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](https://docs.microsoft.com/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="85f16-106">Il existe deux types de fichiers mappés en mémoire :</span><span class="sxs-lookup"><span data-stu-id="85f16-106">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="85f16-107">Fichiers mappés en mémoire persistants</span><span class="sxs-lookup"><span data-stu-id="85f16-107">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="85f16-108">Les fichiers persistants sont des fichiers mappés en mémoire associés à un fichier source sur un disque.</span><span class="sxs-lookup"><span data-stu-id="85f16-108">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="85f16-109">Lorsque le dernier processus a fini de travailler avec le fichier, les données sont enregistrées dans le fichier source sur le disque.</span><span class="sxs-lookup"><span data-stu-id="85f16-109">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="85f16-110">Ces fichiers mappés en mémoire sont adaptés au travail avec des fichiers sources extrêmement volumineux.</span><span class="sxs-lookup"><span data-stu-id="85f16-110">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="85f16-111">Fichiers mappés en mémoire non persistants</span><span class="sxs-lookup"><span data-stu-id="85f16-111">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="85f16-112">Les fichiers non persistants sont des fichiers mappés en mémoire qui ne sont pas associés à un fichier sur un disque.</span><span class="sxs-lookup"><span data-stu-id="85f16-112">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="85f16-113">Lorsque le dernier processus a fini de travailler avec le fichier, les données sont perdues et l'espace mémoire est récupéré par le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-113">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="85f16-114">Ces fichiers sont adaptés à la création d’un partage pour les communications entre processus (IPC).</span><span class="sxs-lookup"><span data-stu-id="85f16-114">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="85f16-115">Processus, vues et gestion de la mémoire</span><span class="sxs-lookup"><span data-stu-id="85f16-115">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="85f16-116">Les fichiers mappés en mémoire peuvent être partagés entre plusieurs processus.</span><span class="sxs-lookup"><span data-stu-id="85f16-116">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="85f16-117">Des processus peuvent mapper le même fichier en mémoire à l’aide d’un nom commun attribué par le processus qui a créé le fichier.</span><span class="sxs-lookup"><span data-stu-id="85f16-117">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="85f16-118">Pour utiliser un fichier mappé en mémoire, vous devez créer une vue de l’intégralité du fichier mappé en mémoire ou une partie de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="85f16-118">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="85f16-119">Vous pouvez également créer plusieurs vues dans la même partie du fichier mappé en mémoire et créer ainsi une mémoire simultanée.</span><span class="sxs-lookup"><span data-stu-id="85f16-119">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="85f16-120">Pour que deux vues restent simultanées, elles doivent être créées à partir du même fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-120">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="85f16-121">Plusieurs vues peuvent également être nécessaires si le fichier est supérieur à la taille de l’espace de mémoire logique de l’application disponible pour le mappage de mémoire (2 Go sur un ordinateur 32 bits).</span><span class="sxs-lookup"><span data-stu-id="85f16-121">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="85f16-122">Il existe deux types de vues : une vue d’accès à Stream et une vue d’accès aléatoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-122">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="85f16-123">Utilisez les vues d’accès à Stream pour un accès séquentiel à un fichier ; c’est recommandé pour les fichiers non persistants et pour IPC.</span><span class="sxs-lookup"><span data-stu-id="85f16-123">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="85f16-124">Les vues d’accès aléatoire sont privilégiées pour l’utilisation de fichiers persistants.</span><span class="sxs-lookup"><span data-stu-id="85f16-124">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="85f16-125">Les fichiers mappés en mémoire sont accessibles via le gestionnaire de mémoire du système d’exploitation. Le fichier est alors automatiquement partitionné en un nombre de pages et consulté en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="85f16-125">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="85f16-126">Vous n’avez pas à gérer vous-même la mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-126">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="85f16-127">L’illustration suivante montre comment plusieurs processus peuvent avoir simultanément plusieurs vues qui se chevauchent dans le même fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-127">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="85f16-128">L’image suivante montre plusieurs vues qui se chevauchent dans un fichier mappé en mémoire :</span><span class="sxs-lookup"><span data-stu-id="85f16-128">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Capture d’écran qui montre des vues dans un fichier mappé en mémoire.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="85f16-130">Programmation avec des fichiers mappés en mémoire</span><span class="sxs-lookup"><span data-stu-id="85f16-130">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="85f16-131">Le tableau suivant fournit un guide pour l’utilisation d’objets de fichier mappé en mémoire et de leurs membres.</span><span class="sxs-lookup"><span data-stu-id="85f16-131">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="85f16-132">Tâche</span><span class="sxs-lookup"><span data-stu-id="85f16-132">Task</span></span>|<span data-ttu-id="85f16-133">Méthodes ou propriétés à utiliser</span><span class="sxs-lookup"><span data-stu-id="85f16-133">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="85f16-134">Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> qui représente un fichier mappé en mémoire persistant à partir d’un fichier sur disque.</span><span class="sxs-lookup"><span data-stu-id="85f16-134">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="85f16-135">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85f16-135"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="85f16-136">Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> qui représente un fichier mappé en mémoire non persistant (pas associé à un fichier sur disque).</span><span class="sxs-lookup"><span data-stu-id="85f16-136">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="85f16-137">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85f16-137"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="85f16-138">- ou -</span><span class="sxs-lookup"><span data-stu-id="85f16-138">- or -</span></span><br /><br /> <span data-ttu-id="85f16-139">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85f16-139"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="85f16-140">Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> d’un fichier mappé en mémoire existant (persistant ou non persistant).</span><span class="sxs-lookup"><span data-stu-id="85f16-140">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="85f16-141">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85f16-141"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="85f16-142">Pour obtenir un objet <xref:System.IO.UnmanagedMemoryStream> pour une vue à accès séquentiel dans le fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-142">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="85f16-143">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85f16-143"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="85f16-144">Pour obtenir un objet <xref:System.IO.UnmanagedMemoryAccessor> pour une vue à accès aléatoire dans un fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-144">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="85f16-145">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="85f16-145"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="85f16-146">Pour obtenir un objet <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> à utiliser avec du code non managé.</span><span class="sxs-lookup"><span data-stu-id="85f16-146">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="85f16-147">Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85f16-147"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="85f16-148">- ou -</span><span class="sxs-lookup"><span data-stu-id="85f16-148">- or -</span></span><br /><br /> <span data-ttu-id="85f16-149">Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85f16-149"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="85f16-150">- ou -</span><span class="sxs-lookup"><span data-stu-id="85f16-150">- or -</span></span><br /><br /> <span data-ttu-id="85f16-151">Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85f16-151"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="85f16-152">Pour différer l’allocation de mémoire jusqu’à ce qu’une vue soit créée (fichiers non persistants uniquement).</span><span class="sxs-lookup"><span data-stu-id="85f16-152">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="85f16-153">(Pour déterminer la taille de page du système actuel, utilisez la propriété <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="85f16-153">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="85f16-154">Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> avec la valeur <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85f16-154"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="85f16-155">- ou -</span><span class="sxs-lookup"><span data-stu-id="85f16-155">- or -</span></span><br /><br /> <span data-ttu-id="85f16-156">Méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> qui ont une énumération <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="85f16-156"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="85f16-157">Sécurité</span><span class="sxs-lookup"><span data-stu-id="85f16-157">Security</span></span>  
 <span data-ttu-id="85f16-158">Vous pouvez appliquer des droits d’accès lorsque vous créez un fichier mappé en mémoire, en utilisant les méthodes suivantes qui prennent une énumération <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> en tant que paramètre :</span><span class="sxs-lookup"><span data-stu-id="85f16-158">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="85f16-159">vous pouvez spécifier des droits d’accès pour l’ouverture d’un fichier mappé en mémoire existant à l’aide des méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> qui prennent un <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="85f16-159">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="85f16-160">Vous pouvez également inclure un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> qui contient des règles d’accès prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="85f16-160">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="85f16-161">Pour appliquer des règles d’accès nouvelles ou modifiées à un fichier mappé en mémoire, utilisez la méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>.</span><span class="sxs-lookup"><span data-stu-id="85f16-161">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="85f16-162">Pour récupérer un accès ou des règles d’audit à partir d’un fichier existant, utilisez la méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>.</span><span class="sxs-lookup"><span data-stu-id="85f16-162">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="85f16-163">Exemples</span><span class="sxs-lookup"><span data-stu-id="85f16-163">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="85f16-164">Fichiers mappés en mémoire persistants</span><span class="sxs-lookup"><span data-stu-id="85f16-164">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="85f16-165">Les méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> créent un fichier mappé en mémoire à partir d’un fichier existant sur le disque.</span><span class="sxs-lookup"><span data-stu-id="85f16-165">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="85f16-166">L’exemple suivant crée une vue mappée en mémoire d’une partie d’un fichier très volumineux et manipule une partie de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="85f16-166">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  
 
[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="85f16-167">L’exemple suivant ouvre le même fichier mappé en mémoire pour un autre processus.</span><span class="sxs-lookup"><span data-stu-id="85f16-167">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="85f16-168">Fichiers mappés en mémoire non persistants</span><span class="sxs-lookup"><span data-stu-id="85f16-168">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="85f16-169">Les méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> et <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> créent un fichier mappé en mémoire qui n’est pas mappé à un fichier existant sur le disque.</span><span class="sxs-lookup"><span data-stu-id="85f16-169">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="85f16-170">L’exemple suivant se compose de trois processus distincts (applications console) qui écrivent des valeurs booléennes dans un fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-170">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="85f16-171">La séquence d’actions suivante se produit :</span><span class="sxs-lookup"><span data-stu-id="85f16-171">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="85f16-172">`Process A` crée le fichier mappé en mémoire et y écrit une valeur.</span><span class="sxs-lookup"><span data-stu-id="85f16-172">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="85f16-173">`Process B` ouvre le fichier mappé en mémoire et y écrit une valeur.</span><span class="sxs-lookup"><span data-stu-id="85f16-173">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="85f16-174">`Process C` ouvre le fichier mappé en mémoire et y écrit une valeur.</span><span class="sxs-lookup"><span data-stu-id="85f16-174">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="85f16-175">`Process A` lit et affiche les valeurs à partir du fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-175">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="85f16-176">Après que `Process A` est terminé avec le fichier mappé en mémoire, ce dernier est immédiatement récupéré par le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="85f16-176">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="85f16-177">Pour exécuter cet exemple, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="85f16-177">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="85f16-178">Compilez les applications et ouvrez trois fenêtres d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="85f16-178">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="85f16-179">Dans la première fenêtre d’invite de commande, exécutez `Process A`.</span><span class="sxs-lookup"><span data-stu-id="85f16-179">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="85f16-180">Dans la deuxième fenêtre d’invite de commande, exécutez `Process B`.</span><span class="sxs-lookup"><span data-stu-id="85f16-180">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="85f16-181">Retournez à `Process A` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="85f16-181">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="85f16-182">Dans la troisième fenêtre d’invite de commande, exécutez `Process C`.</span><span class="sxs-lookup"><span data-stu-id="85f16-182">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="85f16-183">Retournez à `Process A` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="85f16-183">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="85f16-184">La sortie de `Process A` est la suivante :</span><span class="sxs-lookup"><span data-stu-id="85f16-184">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="85f16-185">**Processus A**</span><span class="sxs-lookup"><span data-stu-id="85f16-185">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="85f16-186">**Processus B**</span><span class="sxs-lookup"><span data-stu-id="85f16-186">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="85f16-187">**Processus C**</span><span class="sxs-lookup"><span data-stu-id="85f16-187">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="85f16-188">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="85f16-188">See also</span></span>

- [<span data-ttu-id="85f16-189">Fichier et flux de données E/S</span><span class="sxs-lookup"><span data-stu-id="85f16-189">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
