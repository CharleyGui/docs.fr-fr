---
title: Comment créer un fichier ou un dossier - Guide de programmation C
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: cdcc0a375aa1eca29c024d1e0c9008f337d0c772
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167555"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="7c7ae-102">Comment créer un fichier ou un dossier (Guide de programmation C)</span><span class="sxs-lookup"><span data-stu-id="7c7ae-102">How to create a file or folder (C# Programming Guide)</span></span>
<span data-ttu-id="7c7ae-103">Vous pouvez par programmationcréer un dossier sur votre ordinateur, créer un sous-dossier, créer un fichier dans le sous-dossier et écrire des données dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c7ae-104"> Exemple</span><span class="sxs-lookup"><span data-stu-id="7c7ae-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="7c7ae-105">Si le dossier existe déjà, <xref:System.IO.Directory.CreateDirectory%2A> est sans effet et aucune exception n’est levée.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="7c7ae-106">Toutefois, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> remplace un fichier existant par un nouveau fichier.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="7c7ae-107">L’exemple utilise une instruction `if`-`else` pour éviter qu’un fichier existant soit pas remplacé.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="7c7ae-108">En apportant les modifications suivantes dans l’exemple, vous pouvez spécifier des résultats différents si un fichier avec un nom spécifique existe déjà.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="7c7ae-109">Si un tel fichier n’existe pas, le code en crée un.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="7c7ae-110">Si un tel fichier existe, le code ajoute des données à ce fichier.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="7c7ae-111">Spécifiez un nom de fichier non aléatoire.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="7c7ae-112">Remplacez l’instruction `if`-`else` par l’instruction `using` dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="7c7ae-113">Exécutez l’exemple plusieurs fois pour vérifier que les données sont ajoutées au fichier à chaque fois.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="7c7ae-114">Pour découvrir d’autres valeurs `FileMode` que vous pouvez essayer, consultez <xref:System.IO.FileMode>.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="7c7ae-115">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="7c7ae-116">Le nom du dossier est mal formé.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-116">The folder name is malformed.</span></span> <span data-ttu-id="7c7ae-117">Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (classe <xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="7c7ae-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="7c7ae-118">Utilisez la classe <xref:System.IO.Path> pour créer des noms de chemin valides.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="7c7ae-119">Le dossier parent du dossier à créer est en lecture seule (classe <xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="7c7ae-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="7c7ae-120">Le nom du dossier est `null` (classe <xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="7c7ae-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="7c7ae-121">Le nom du dossier est trop long (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="7c7ae-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="7c7ae-122">Le nom du dossier est uniquement un signe deux-points, « : » (classe <xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="7c7ae-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7c7ae-123">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7c7ae-123">.NET Framework Security</span></span>  
 <span data-ttu-id="7c7ae-124">Une instance de la classe <xref:System.Security.SecurityException> peut être levée dans les situations de confiance partielle.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="7c7ae-125">Si vous n’êtes pas autorisé à créer le dossier, l’exemple lève une instance de la classe <xref:System.UnauthorizedAccessException>.</span><span class="sxs-lookup"><span data-stu-id="7c7ae-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c7ae-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c7ae-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="7c7ae-127">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7c7ae-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7c7ae-128">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="7c7ae-128">File System and the Registry (C# Programming Guide)</span></span>](./index.md)
