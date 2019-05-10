---
title: 'Procédure : Écrire des données de l’objet dans un fichier XML (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
ms.openlocfilehash: 17f8463a4b905028d37a2e005562867f87f4bd2b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624374"
---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="8276c-102">Procédure : Écrire des données de l’objet dans un fichier XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8276c-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="8276c-103">Cet exemple écrit l’objet d’une classe dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="8276c-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8276c-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="8276c-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8276c-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="8276c-105">Compiling the Code</span></span>  
 <span data-ttu-id="8276c-106">La classe doit disposer d’un constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="8276c-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="8276c-107">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="8276c-107">Robust Programming</span></span>  
 <span data-ttu-id="8276c-108">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="8276c-108">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="8276c-109">La classe qui est sérialisée n’a pas de constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="8276c-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="8276c-110">Le fichier existe et est en lecture seule (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="8276c-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="8276c-111">Le chemin est trop long (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="8276c-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="8276c-112">Le disque est plein (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="8276c-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="8276c-113">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8276c-113">.NET Framework Security</span></span>  
 <span data-ttu-id="8276c-114">Cet exemple crée un fichier s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="8276c-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="8276c-115">Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier.</span><span class="sxs-lookup"><span data-stu-id="8276c-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="8276c-116">Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, qui est une autorisation de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="8276c-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="8276c-117">Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier, plutôt que l’autorisation `Create` sur un dossier.</span><span class="sxs-lookup"><span data-stu-id="8276c-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8276c-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8276c-118">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="8276c-119">Guide pratique pour Lire les données d’objet à partir d’un fichier XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8276c-119">How to: Read Object Data from an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)
- [<span data-ttu-id="8276c-120">Sérialisation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8276c-120">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
