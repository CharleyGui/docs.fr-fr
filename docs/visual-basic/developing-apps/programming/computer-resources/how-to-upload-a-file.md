---
title: 'Comment : transférer un fichier'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 52b731606c74ab7ff06a42dfdbe078616ba33d88
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345558"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="fc7e5-102">Comment : transférer un fichier dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fc7e5-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="fc7e5-103">Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> pour charger un fichier et le stocker dans un emplacement distant.</span><span class="sxs-lookup"><span data-stu-id="fc7e5-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="fc7e5-104">Si le paramètre `ShowUI` a la valeur `True`, une boîte de dialogue s’affiche pour indiquer la progression du chargement et permettre aux utilisateurs d’annuler l’opération.</span><span class="sxs-lookup"><span data-stu-id="fc7e5-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="fc7e5-105">Pour charger un fichier</span><span class="sxs-lookup"><span data-stu-id="fc7e5-105">To upload a file</span></span>  
  
- <span data-ttu-id="fc7e5-106">Utilisez la méthode `UploadFile` pour charger un fichier, en spécifiant l’emplacement du fichier source et l’emplacement du répertoire cible sous forme de chaîne ou d’URI (Uniform Resource Identifier). Cet exemple charge le fichier `Order.txt` sur `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="fc7e5-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="fc7e5-107">Pour charger un fichier et afficher la progression de l’opération</span><span class="sxs-lookup"><span data-stu-id="fc7e5-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="fc7e5-108">Utilisez la méthode `UploadFile` pour charger un fichier, en spécifiant l’emplacement du fichier source et l’emplacement du répertoire cible sous forme de chaîne ou d’URI.</span><span class="sxs-lookup"><span data-stu-id="fc7e5-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="fc7e5-109">Cet exemple charge le fichier `Order.txt` sur `http://www.cohowinery.com/uploads.aspx` sans fournir de nom d’utilisateur ou de mot de passe, affiche la progression du chargement, et présente un délai d’attente de 500 millisecondes.</span><span class="sxs-lookup"><span data-stu-id="fc7e5-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="fc7e5-110">Pour charger un fichier en fournissant un nom d’utilisateur et un mot de passe</span><span class="sxs-lookup"><span data-stu-id="fc7e5-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="fc7e5-111">Utilisez la méthode `UploadFile` pour charger un fichier, en spécifiant l’emplacement du fichier source et l’emplacement du répertoire cible sous forme de chaîne ou d’URI, et en spécifiant le nom d’utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="fc7e5-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="fc7e5-112">Cet exemple charge le fichier `Order.txt` sur `http://www.cohowinery.com/uploads.aspx`, en fournissant le nom d’utilisateur `anonymous` et un mot de passe vide.</span><span class="sxs-lookup"><span data-stu-id="fc7e5-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fc7e5-113">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="fc7e5-113">Robust Programming</span></span>  

 <span data-ttu-id="fc7e5-114">Les conditions suivantes peuvent lever une exception :</span><span class="sxs-lookup"><span data-stu-id="fc7e5-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="fc7e5-115">Le chemin local n’est pas valide (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="fc7e5-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="fc7e5-116">L’authentification a échoué (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="fc7e5-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="fc7e5-117">La connexion a expiré (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="fc7e5-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc7e5-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc7e5-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="fc7e5-119">Guide pratique : télécharger un fichier</span><span class="sxs-lookup"><span data-stu-id="fc7e5-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="fc7e5-120">Guide pratique : analyser des chemins d’accès</span><span class="sxs-lookup"><span data-stu-id="fc7e5-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
