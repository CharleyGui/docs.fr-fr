---
title: 'Procédure : écrire du texte dans des fichiers du répertoire Mes documents'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- examples [Visual Basic], text files
- writing to files [Visual Basic], in My Documents
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
ms.openlocfilehash: bb3a9bdc44f86fbcdb3c56ee088740efdfebe95d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546456"
---
# <a name="how-to-write-text-to-files-in-the-my-documents-directory-in-visual-basic"></a><span data-ttu-id="6f441-102">Comment : insérer du texte dans les fichiers du répertoire Mes Documents dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6f441-102">How to: Write Text to Files in the My Documents Directory in Visual Basic</span></span>

<span data-ttu-id="6f441-103">L’objet `My.Computer.FileSystem.SpecialDirectories` vous permet d’accéder à des répertoires spéciaux, comme le répertoire **Mes documents**.</span><span class="sxs-lookup"><span data-stu-id="6f441-103">The `My.Computer.FileSystem.SpecialDirectories` object allows you to access special directories, such as the **MyDocuments** directory.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="6f441-104">Procédure</span><span class="sxs-lookup"><span data-stu-id="6f441-104">Procedure</span></span>  
  
#### <a name="to-write-new-text-files-in-the-my-documents-directory"></a><span data-ttu-id="6f441-105">Pour écrire de nouveaux fichiers texte dans le répertoire Mes Documents</span><span class="sxs-lookup"><span data-stu-id="6f441-105">To write new text files in the My Documents directory</span></span>  
  
1. <span data-ttu-id="6f441-106">Utilisez la propriété `My.Computer.FileSystem.SpecialDirectories.MyDocuments` pour fournir le chemin.</span><span class="sxs-lookup"><span data-stu-id="6f441-106">Use the `My.Computer.FileSystem.SpecialDirectories.MyDocuments` property to supply the path.</span></span>  
  
     [!code-vb[VbFileIOWrite#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#1)]  
  
2. <span data-ttu-id="6f441-107">Utilisez la méthode `WriteAllText` pour écrire du texte dans le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="6f441-107">Use the `WriteAllText` method to write text to the specified file.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#14)]  
  
## <a name="example"></a><span data-ttu-id="6f441-108"> Exemple</span><span class="sxs-lookup"><span data-stu-id="6f441-108">Example</span></span>  

 [!code-vb[VbFileIOWrite#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOWrite/VB/Class1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6f441-109">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6f441-109">Compiling the Code</span></span>  

 <span data-ttu-id="6f441-110">Remplacez `test.txt` par le nom du fichier dans lequel vous voulez écrire.</span><span class="sxs-lookup"><span data-stu-id="6f441-110">Replace `test.txt` with the name of the file you want to write to.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6f441-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="6f441-111">Robust Programming</span></span>  

 <span data-ttu-id="6f441-112">Ce code lève de nouveau toutes les exceptions qui peuvent se produire lors de l’écriture de texte dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="6f441-112">This code rethrows all the exceptions that may occur when writing text to the file.</span></span> <span data-ttu-id="6f441-113">Vous pouvez réduire la probabilité d’exceptions en utilisant des contrôles Windows Forms comme les composants [OpenFileDialog](/dotnet/desktop/winforms/controls/openfiledialog-component-windows-forms) et [SaveFileDialog](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms) qui limitent les choix de l’utilisateur à des noms de fichier valides.</span><span class="sxs-lookup"><span data-stu-id="6f441-113">You can reduce the likelihood of exceptions by using Windows Forms controls such as the [OpenFileDialog](/dotnet/desktop/winforms/controls/openfiledialog-component-windows-forms) and the [SaveFileDialog](/dotnet/desktop/winforms/controls/savefiledialog-component-windows-forms) components that limit the user choices to valid file names.</span></span> <span data-ttu-id="6f441-114">Toutefois, l’utilisation de ces contrôles n’est pas infaillible.</span><span class="sxs-lookup"><span data-stu-id="6f441-114">Using these controls is not foolproof, however.</span></span> <span data-ttu-id="6f441-115">Le système de fichiers peut changer entre le moment où l’utilisateur sélectionne un fichier et celui où le code s’exécute.</span><span class="sxs-lookup"><span data-stu-id="6f441-115">The file system can change between the time the user selects a file and the time that the code executes.</span></span> <span data-ttu-id="6f441-116">La gestion des exceptions est donc presque toujours nécessaire quand vous utilisez des fichiers.</span><span class="sxs-lookup"><span data-stu-id="6f441-116">Exception handling is therefore nearly always necessary when with working with files.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6f441-117">Sécurité du .NET Framework</span><span class="sxs-lookup"><span data-stu-id="6f441-117">.NET Framework Security</span></span>  

 <span data-ttu-id="6f441-118">Si vous l’exécutez dans un contexte de confiance partielle, le code peut lever une exception en raison de privilèges insuffisants.</span><span class="sxs-lookup"><span data-stu-id="6f441-118">If you are running in a partial-trust context, the code might throw an exception due to insufficient privileges.</span></span> <span data-ttu-id="6f441-119">Pour plus d’informations, consultez [Notions fondamentales de la sécurité d’accès du code](../../../../framework/misc/code-access-security-basics.md).</span><span class="sxs-lookup"><span data-stu-id="6f441-119">For more information, see [Code Access Security Basics](../../../../framework/misc/code-access-security-basics.md).</span></span>  
  
 <span data-ttu-id="6f441-120">Cet exemple crée un fichier.</span><span class="sxs-lookup"><span data-stu-id="6f441-120">This example creates a new file.</span></span> <span data-ttu-id="6f441-121">Si une application doit créer un fichier, elle doit disposer de l’autorisation de création sur le dossier.</span><span class="sxs-lookup"><span data-stu-id="6f441-121">If an application needs to create a file, that application needs Create permission for the folder.</span></span> <span data-ttu-id="6f441-122">Les autorisations sont définies à l’aide des listes de contrôle d’accès.</span><span class="sxs-lookup"><span data-stu-id="6f441-122">Permissions are set using access control lists.</span></span> <span data-ttu-id="6f441-123">Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation d’écriture, ce qui représente une autorisation inférieure.</span><span class="sxs-lookup"><span data-stu-id="6f441-123">If the file already exists, the application needs only Write permission, a lesser privilege.</span></span> <span data-ttu-id="6f441-124">Quand cela est possible, il est plus sûr de créer le fichier pendant le déploiement et de n’accorder les privilèges de lecture que sur un seul fichier, plutôt que d’accorder des privilèges de création sur un dossier.</span><span class="sxs-lookup"><span data-stu-id="6f441-124">Where possible, it is more secure to create the file during deployment, and only grant Read privileges to a single file, rather than to grant Create privileges for a folder.</span></span> <span data-ttu-id="6f441-125">En outre, il est plus sûr d’écrire des données dans des dossiers utilisateur que dans le dossier racine ou le dossier **Program Files** .</span><span class="sxs-lookup"><span data-stu-id="6f441-125">Also, it is more secure to write data to user folders than to the root folder or the **Program Files** folder.</span></span> <span data-ttu-id="6f441-126">Pour plus d’informations, consultez [Vue d’ensemble de la technologie ACL](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="6f441-126">For more information, see [ACL Technology Overview](/previous-versions/dotnet/netframework-4.0/ms229742(v=vs.100)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f441-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6f441-127">See also</span></span>

- <xref:System.IO.Path.Combine%2A?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Computer>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>
