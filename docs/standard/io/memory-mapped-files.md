---
title: Fichiers mappés en mémoire
description: Explorez les fichiers mappés en mémoire dans .NET, qui contiennent le contenu du fichier dans la mémoire virtuelle, et autorisez les applications à modifier le fichier en écrivant directement dans la mémoire.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- memory-mapped files
- inter-process communication
ms.assetid: a483d1b5-64aa-45b6-86ef-11b859f7f02e
ms.openlocfilehash: 74d821aff8308618f7c0efeb1b453db8214b877e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555944"
---
# <a name="memory-mapped-files"></a><span data-ttu-id="fe512-103">Fichiers mappés en mémoire</span><span class="sxs-lookup"><span data-stu-id="fe512-103">Memory-Mapped Files</span></span>
<span data-ttu-id="fe512-104">Un fichier mappé en mémoire comporte le contenu d'un fichier en mémoire virtuelle.</span><span class="sxs-lookup"><span data-stu-id="fe512-104">A memory-mapped file contains the contents of a file in virtual memory.</span></span> <span data-ttu-id="fe512-105">Ce mappage entre un fichier et un espace mémoire permet à une application incluant plusieurs processus de modifier le fichier en lisant et en écrivant directement dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-105">This mapping between a file and memory space enables an application, including multiple processes, to modify the file by reading and writing directly to the memory.</span></span> <span data-ttu-id="fe512-106">À compter de .NET Framework 4, vous pouvez utiliser du code managé pour accéder aux fichiers mappés en mémoire de la même façon que les fonctions Windows natives accèdent à des fichiers mappés en mémoire, comme décrit dans [Gestion des fichiers mappés en mémoire](/previous-versions/ms810613(v=msdn.10)).</span><span class="sxs-lookup"><span data-stu-id="fe512-106">Starting with the .NET Framework 4, you can use managed code to access memory-mapped files in the same way that native Windows functions access memory-mapped files, as described in [Managing Memory-Mapped Files](/previous-versions/ms810613(v=msdn.10)).</span></span>  
  
 <span data-ttu-id="fe512-107">Il existe deux types de fichiers mappés en mémoire :</span><span class="sxs-lookup"><span data-stu-id="fe512-107">There are two types of memory-mapped files:</span></span>  
  
- <span data-ttu-id="fe512-108">Fichiers mappés en mémoire persistants</span><span class="sxs-lookup"><span data-stu-id="fe512-108">Persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="fe512-109">Les fichiers persistants sont des fichiers mappés en mémoire associés à un fichier source sur un disque.</span><span class="sxs-lookup"><span data-stu-id="fe512-109">Persisted files are memory-mapped files that are associated with a source file on a disk.</span></span> <span data-ttu-id="fe512-110">Lorsque le dernier processus a fini de travailler avec le fichier, les données sont enregistrées dans le fichier source sur le disque.</span><span class="sxs-lookup"><span data-stu-id="fe512-110">When the last process has finished working with the file, the data is saved to the source file on the disk.</span></span> <span data-ttu-id="fe512-111">Ces fichiers mappés en mémoire sont adaptés au travail avec des fichiers sources extrêmement volumineux.</span><span class="sxs-lookup"><span data-stu-id="fe512-111">These memory-mapped files are suitable for working with extremely large source files.</span></span>  
  
- <span data-ttu-id="fe512-112">Fichiers mappés en mémoire non persistants</span><span class="sxs-lookup"><span data-stu-id="fe512-112">Non-persisted memory-mapped files</span></span>  
  
     <span data-ttu-id="fe512-113">Les non fichiers persistants sont des fichiers mappés en mémoire associés à un fichier sur un disque.</span><span class="sxs-lookup"><span data-stu-id="fe512-113">Non-persisted files are memory-mapped files that are not associated with a file on a disk.</span></span> <span data-ttu-id="fe512-114">Lorsque le dernier processus a fini de travailler avec le fichier, les données sont perdues et l'espace mémoire est récupéré par le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-114">When the last process has finished working with the file, the data is lost and the file is reclaimed by garbage collection.</span></span> <span data-ttu-id="fe512-115">Ces fichiers sont adaptés à la création d’une mémoire partagée pour les communications entre processus (IPC).</span><span class="sxs-lookup"><span data-stu-id="fe512-115">These files are suitable for creating shared memory for inter-process communications (IPC).</span></span>  
  
## <a name="processes-views-and-managing-memory"></a><span data-ttu-id="fe512-116">Processus, vues et gestion de la mémoire</span><span class="sxs-lookup"><span data-stu-id="fe512-116">Processes, Views, and Managing Memory</span></span>  
 <span data-ttu-id="fe512-117">Les fichiers mappés en mémoire ne peuvent pas être partagé entre plusieurs processus.</span><span class="sxs-lookup"><span data-stu-id="fe512-117">Memory-mapped files can be shared across multiple processes.</span></span> <span data-ttu-id="fe512-118">Des processus peuvent être mappés dans le même fichier mappé en mémoire à l’aide d’un nom commun attribué par le processus qui a créé le fichier.</span><span class="sxs-lookup"><span data-stu-id="fe512-118">Processes can map to the same memory-mapped file by using a common name that is assigned by the process that created the file.</span></span>  
  
 <span data-ttu-id="fe512-119">Pour utiliser un fichier mappé en mémoire, vous devez créer une vue de l’intégralité du fichier mappé en mémoire ou une partie de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="fe512-119">To work with a memory-mapped file, you must create a view of the entire memory-mapped file or a part of it.</span></span> <span data-ttu-id="fe512-120">Vous pouvez également créer plusieurs vues dans la même partie du fichier mappé en mémoire et créer ainsi une mémoire simultanée.</span><span class="sxs-lookup"><span data-stu-id="fe512-120">You can also create multiple views to the same part of the memory-mapped file, thereby creating concurrent memory.</span></span> <span data-ttu-id="fe512-121">Pour que deux vues restent simultanées, elles doivent être créées à partir du même fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-121">For two views to remain concurrent, they have to be created from the same memory-mapped file.</span></span>  
  
 <span data-ttu-id="fe512-122">Plusieurs vues peuvent également être nécessaires si le fichier est supérieur à la taille de l’espace de mémoire logique de l’application disponible pour le mappage de mémoire (2 Go sur un ordinateur 32 bits).</span><span class="sxs-lookup"><span data-stu-id="fe512-122">Multiple views may also be necessary if the file is greater than the size of the application’s logical memory space available for memory mapping (2 GB on a 32-bit computer).</span></span>  
  
 <span data-ttu-id="fe512-123">Il existe deux types de vues : une vue d’accès à Stream et une vue d’accès aléatoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-123">There are two types of views: stream access view and random access view.</span></span> <span data-ttu-id="fe512-124">Utilisez les vues d’accès à Stream pour un accès séquentiel à un fichier ; c’est recommandé pour les fichiers non persistants et pour IPC.</span><span class="sxs-lookup"><span data-stu-id="fe512-124">Use stream access views for sequential access to a file; this is recommended for non-persisted files and IPC.</span></span> <span data-ttu-id="fe512-125">Les vues d’accès aléatoire sont privilégiées pour l’utilisation de fichiers persistants.</span><span class="sxs-lookup"><span data-stu-id="fe512-125">Random access views are preferred for working with persisted files.</span></span>  
  
 <span data-ttu-id="fe512-126">Les fichiers mappés en mémoire sont accessibles via le gestionnaire de mémoire du système d’exploitation. Le fichier est alors automatiquement partitionné en un nombre de pages et consulté en fonction des besoins.</span><span class="sxs-lookup"><span data-stu-id="fe512-126">Memory-mapped files are accessed through the operating system’s memory manager, so the file is automatically partitioned into a number of pages and accessed as needed.</span></span> <span data-ttu-id="fe512-127">Vous n’avez pas à gérer vous-même la mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-127">You do not have to handle the memory management yourself.</span></span>  
  
 <span data-ttu-id="fe512-128">L’illustration suivante montre comment plusieurs processus peuvent avoir simultanément plusieurs vues qui se chevauchent dans le même fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-128">The following illustration shows how multiple processes can have multiple and overlapping views to the same memory-mapped file at the same time.</span></span>

 <span data-ttu-id="fe512-129">L’image suivante montre plusieurs vues qui se chevauchent dans un fichier mappé en mémoire :</span><span class="sxs-lookup"><span data-stu-id="fe512-129">The following image shows multiple and overlapped views to a memory-mapped file:</span></span>  
  
 ![Capture d’écran qui montre des vues dans un fichier mappé en mémoire.](./media/memory-mapped-files/memory-map-persist-file.png)  
  
## <a name="programming-with-memory-mapped-files"></a><span data-ttu-id="fe512-131">Programmation avec des fichiers mappés en mémoire</span><span class="sxs-lookup"><span data-stu-id="fe512-131">Programming with Memory-Mapped Files</span></span>  
 <span data-ttu-id="fe512-132">Le tableau suivant fournit un guide pour l’utilisation d’objets de fichier mappé en mémoire et de leurs membres.</span><span class="sxs-lookup"><span data-stu-id="fe512-132">The following table provides a guide for using memory-mapped file objects and their members.</span></span>  
  
|<span data-ttu-id="fe512-133">Tâche</span><span class="sxs-lookup"><span data-stu-id="fe512-133">Task</span></span>|<span data-ttu-id="fe512-134">Méthodes ou propriétés à utiliser</span><span class="sxs-lookup"><span data-stu-id="fe512-134">Methods or properties to use</span></span>|  
|----------|----------------------------------|  
|<span data-ttu-id="fe512-135">Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> qui représente un fichier mappé en mémoire persistant à partir d’un fichier sur disque.</span><span class="sxs-lookup"><span data-stu-id="fe512-135">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a persisted memory-mapped file from a file on disk.</span></span>|<span data-ttu-id="fe512-136">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe512-136"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="fe512-137">Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> qui représente un fichier mappé en mémoire non persistant (pas associé à un fichier sur disque).</span><span class="sxs-lookup"><span data-stu-id="fe512-137">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object that represents a non-persisted memory-mapped file (not associated with a file on disk).</span></span>|<span data-ttu-id="fe512-138">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe512-138"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType> method.</span></span><br /><br /> <span data-ttu-id="fe512-139">- ou -</span><span class="sxs-lookup"><span data-stu-id="fe512-139">- or -</span></span><br /><br /> <span data-ttu-id="fe512-140">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe512-140"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="fe512-141">Pour obtenir un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> d’un fichier mappé en mémoire existant (persistant ou non persistant).</span><span class="sxs-lookup"><span data-stu-id="fe512-141">To obtain a <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> object of an existing memory-mapped file (either persisted or non-persisted).</span></span>|<span data-ttu-id="fe512-142">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe512-142"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="fe512-143">Pour obtenir un objet <xref:System.IO.UnmanagedMemoryStream> pour une vue à accès séquentiel dans le fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-143">To obtain a <xref:System.IO.UnmanagedMemoryStream> object for a sequentially accessed view to the memory-mapped file.</span></span>|<span data-ttu-id="fe512-144">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe512-144"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewStream%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="fe512-145">Pour obtenir un objet <xref:System.IO.UnmanagedMemoryAccessor> pour une vue à accès aléatoire dans un fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-145">To obtain a <xref:System.IO.UnmanagedMemoryAccessor> object for a random access view to a memory-mapped fie.</span></span>|<span data-ttu-id="fe512-146">Méthode<xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe512-146"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateViewAccessor%2A?displayProperty=nameWithType> method.</span></span>|  
|<span data-ttu-id="fe512-147">Pour obtenir un objet <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> à utiliser avec du code non managé.</span><span class="sxs-lookup"><span data-stu-id="fe512-147">To obtain a <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> object to use with unmanaged code.</span></span>|<span data-ttu-id="fe512-148">Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe512-148"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SafeMemoryMappedFileHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="fe512-149">- ou -</span><span class="sxs-lookup"><span data-stu-id="fe512-149">- or -</span></span><br /><br /> <span data-ttu-id="fe512-150">Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe512-150"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewAccessor.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span><br /><br /> <span data-ttu-id="fe512-151">- ou -</span><span class="sxs-lookup"><span data-stu-id="fe512-151">- or -</span></span><br /><br /> <span data-ttu-id="fe512-152">Propriété <xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe512-152"><xref:System.IO.MemoryMappedFiles.MemoryMappedViewStream.SafeMemoryMappedViewHandle%2A?displayProperty=nameWithType> property.</span></span>|  
|<span data-ttu-id="fe512-153">Pour différer l’allocation de mémoire jusqu’à ce qu’une vue soit créée (fichiers non persistants uniquement).</span><span class="sxs-lookup"><span data-stu-id="fe512-153">To delay allocating memory until a view is created (non-persisted files only).</span></span><br /><br /> <span data-ttu-id="fe512-154">(Pour déterminer la taille de page du système actuel, utilisez la propriété <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType>.)</span><span class="sxs-lookup"><span data-stu-id="fe512-154">(To determine the current system page size, use the <xref:System.Environment.SystemPageSize%2A?displayProperty=nameWithType> property.)</span></span>|<span data-ttu-id="fe512-155">Méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> avec la valeur <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe512-155"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> method with the <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions.DelayAllocatePages?displayProperty=nameWithType> value.</span></span><br /><br /> <span data-ttu-id="fe512-156">- ou -</span><span class="sxs-lookup"><span data-stu-id="fe512-156">- or -</span></span><br /><br /> <span data-ttu-id="fe512-157">Méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> qui ont une énumération <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="fe512-157"><xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods that have a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileOptions> enumeration as a parameter.</span></span>|  
  
### <a name="security"></a><span data-ttu-id="fe512-158">Sécurité</span><span class="sxs-lookup"><span data-stu-id="fe512-158">Security</span></span>  
 <span data-ttu-id="fe512-159">Vous pouvez appliquer des droits d’accès lorsque vous créez un fichier mappé en mémoire, en utilisant les méthodes suivantes qui prennent une énumération <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> en tant que paramètre :</span><span class="sxs-lookup"><span data-stu-id="fe512-159">You can apply access rights when you create a memory-mapped file, by using the following methods that take a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileAccess> enumeration as a parameter:</span></span>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A?displayProperty=nameWithType>  
  
- <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="fe512-160">vous pouvez spécifier des droits d’accès pour l’ouverture d’un fichier mappé en mémoire existant à l’aide des méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> qui prennent un <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> en tant que paramètre.</span><span class="sxs-lookup"><span data-stu-id="fe512-160">You can specify access rights for opening an existing memory-mapped file by using the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.OpenExisting%2A> methods that take an <xref:System.IO.MemoryMappedFiles.MemoryMappedFileRights> as a parameter.</span></span>  
  
 <span data-ttu-id="fe512-161">Vous pouvez également inclure un objet <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> qui contient des règles d’accès prédéfinies.</span><span class="sxs-lookup"><span data-stu-id="fe512-161">In addition, you can include a <xref:System.IO.MemoryMappedFiles.MemoryMappedFileSecurity> object that contains predefined access rules.</span></span>  
  
 <span data-ttu-id="fe512-162">Pour appliquer des règles d’accès nouvelles ou modifiées à un fichier mappé en mémoire, utilisez la méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe512-162">To apply new or changed access rules to a memory-mapped file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.SetAccessControl%2A> method.</span></span> <span data-ttu-id="fe512-163">Pour récupérer un accès ou des règles d’audit à partir d’un fichier existant, utilisez la méthode <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A>.</span><span class="sxs-lookup"><span data-stu-id="fe512-163">To retrieve access or audit rules from an existing file, use the <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.GetAccessControl%2A> method.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="fe512-164">Exemples</span><span class="sxs-lookup"><span data-stu-id="fe512-164">Examples</span></span>  
  
### <a name="persisted-memory-mapped-files"></a><span data-ttu-id="fe512-165">Fichiers mappés en mémoire persistants</span><span class="sxs-lookup"><span data-stu-id="fe512-165">Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="fe512-166">Les méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> créent un fichier mappé en mémoire à partir d’un fichier existant sur le disque.</span><span class="sxs-lookup"><span data-stu-id="fe512-166">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateFromFile%2A> methods create a memory-mapped file from an existing file on disk.</span></span>  
  
 <span data-ttu-id="fe512-167">L’exemple suivant crée une vue mappée en mémoire d’une partie d’un fichier très volumineux et manipule une partie de ce dernier.</span><span class="sxs-lookup"><span data-stu-id="fe512-167">The following example creates a memory-mapped view of a part of an extremely large file and manipulates a portion of it.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.CreateFromFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.createfromfile/vb/program.vb#1)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

 <span data-ttu-id="fe512-168">L’exemple suivant ouvre le même fichier mappé en mémoire pour un autre processus.</span><span class="sxs-lookup"><span data-stu-id="fe512-168">The following example opens the same memory-mapped file for another process.</span></span>  
  
 [!code-csharp[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/cs/program.cs#1)]
 [!code-vb[MemoryMappedFiles.MemoryMappedFile.OpenExisting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/memorymappedfiles.memorymappedfile.openexisting/vb/program.vb#1)]  
  
### <a name="non-persisted-memory-mapped-files"></a><span data-ttu-id="fe512-169">Fichiers mappés en mémoire non persistants</span><span class="sxs-lookup"><span data-stu-id="fe512-169">Non-Persisted Memory-Mapped Files</span></span>  
 <span data-ttu-id="fe512-170">Les méthodes <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> et <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> créent un fichier mappé en mémoire qui n’est pas mappé à un fichier existant sur le disque.</span><span class="sxs-lookup"><span data-stu-id="fe512-170">The <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateNew%2A> and <xref:System.IO.MemoryMappedFiles.MemoryMappedFile.CreateOrOpen%2A> methods create a memory-mapped file that is not mapped to an existing file on disk.</span></span>  
  
 <span data-ttu-id="fe512-171">L’exemple suivant se compose de trois processus distincts (applications console) qui écrivent des valeurs booléennes dans un fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-171">The following example consists of three separate processes (console applications) that write Boolean values to a memory-mapped file.</span></span> <span data-ttu-id="fe512-172">La séquence d’actions suivante se produit :</span><span class="sxs-lookup"><span data-stu-id="fe512-172">The following sequence of actions occur:</span></span>  
  
1. <span data-ttu-id="fe512-173">`Process A` crée le fichier mappé en mémoire et y écrit une valeur.</span><span class="sxs-lookup"><span data-stu-id="fe512-173">`Process A` creates the memory-mapped file and writes a value to it.</span></span>  
  
2. <span data-ttu-id="fe512-174">`Process B` ouvre le fichier mappé en mémoire et y écrit une valeur.</span><span class="sxs-lookup"><span data-stu-id="fe512-174">`Process B` opens the memory-mapped file and writes a value to it.</span></span>  
  
3. <span data-ttu-id="fe512-175">`Process C` ouvre le fichier mappé en mémoire et y écrit une valeur.</span><span class="sxs-lookup"><span data-stu-id="fe512-175">`Process C` opens the memory-mapped file and writes a value to it.</span></span>  
  
4. <span data-ttu-id="fe512-176">`Process A` lit et affiche les valeurs à partir du fichier mappé en mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-176">`Process A` reads and displays the values from the memory-mapped file.</span></span>  
  
5. <span data-ttu-id="fe512-177">Après que `Process A` est terminé avec le fichier mappé en mémoire, ce dernier est immédiatement récupéré par le nettoyage de la mémoire.</span><span class="sxs-lookup"><span data-stu-id="fe512-177">After `Process A` is finished with the memory-mapped file, the file is immediately reclaimed by garbage collection.</span></span>  
  
 <span data-ttu-id="fe512-178">Pour exécuter cet exemple, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="fe512-178">To run this example, do the following:</span></span>  
  
1. <span data-ttu-id="fe512-179">Compilez les applications et ouvrez trois fenêtres d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="fe512-179">Compile the applications and open three Command Prompt windows.</span></span>  
  
2. <span data-ttu-id="fe512-180">Dans la première fenêtre d’invite de commande, exécutez `Process A`.</span><span class="sxs-lookup"><span data-stu-id="fe512-180">In the first Command Prompt window, run `Process A`.</span></span>  
  
3. <span data-ttu-id="fe512-181">Dans la deuxième fenêtre d’invite de commande, exécutez `Process B`.</span><span class="sxs-lookup"><span data-stu-id="fe512-181">In the second Command Prompt window, run `Process B`.</span></span>  
  
4. <span data-ttu-id="fe512-182">Retournez à `Process A` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="fe512-182">Return to `Process A` and press ENTER.</span></span>  
  
5. <span data-ttu-id="fe512-183">Dans la troisième fenêtre d’invite de commande, exécutez `Process C`.</span><span class="sxs-lookup"><span data-stu-id="fe512-183">In the third Command Prompt window, run `Process C`.</span></span>  
  
6. <span data-ttu-id="fe512-184">Retournez à `Process A` et appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="fe512-184">Return to `Process A` and press ENTER.</span></span>  
  
 <span data-ttu-id="fe512-185">La sortie de `Process A` est la suivante :</span><span class="sxs-lookup"><span data-stu-id="fe512-185">The output of `Process A` is as follows:</span></span>  
  
```console  
Start Process B and press ENTER to continue.  
Start Process C and press ENTER to continue.  
Process A says: True  
Process B says: False  
Process C says: True  
```  
  
 <span data-ttu-id="fe512-186">**Processus A**</span><span class="sxs-lookup"><span data-stu-id="fe512-186">**Process A**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_X#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_x/vb/program.vb#1)]  
  
 <span data-ttu-id="fe512-187">**Processus B**</span><span class="sxs-lookup"><span data-stu-id="fe512-187">**Process B**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_A#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_a/vb/program.vb#1)]  
  
 <span data-ttu-id="fe512-188">**Processus C**</span><span class="sxs-lookup"><span data-stu-id="fe512-188">**Process C**</span></span>  
  
 [!code-csharp[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/cs/program.cs#1)]
 [!code-vb[System.IO.MemoryMappedFiles_IPC_B#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.memorymappedfiles_ipc_b/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="fe512-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fe512-189">See also</span></span>

- [<span data-ttu-id="fe512-190">E/s de fichier et de flux</span><span class="sxs-lookup"><span data-stu-id="fe512-190">File and Stream I/O</span></span>](index.md)
