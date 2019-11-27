---
title: 'Comment : lire des données d’objet à partir d’un fichier XML'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: c997af4729a24a6b5bd5b22d0153860cff3282d7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346434"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="fbe71-102">Procédure : lire des données d’objet à partir d’un fichier XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbe71-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="fbe71-103">Cet exemple lit des données d’objet écrites précédemment dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="fbe71-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbe71-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="fbe71-104">Example</span></span>  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fbe71-105">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="fbe71-105">Compiling the Code</span></span>  
 <span data-ttu-id="fbe71-106">Remplacez le nom du fichier « c:\temp\SerializationOverview.xml » par le nom du fichier qui contient les données sérialisées.</span><span class="sxs-lookup"><span data-stu-id="fbe71-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="fbe71-107">Pour plus d’informations sur la sérialisation des données, consultez [Comment : écrire des données d’objet dans un fichier XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span><span class="sxs-lookup"><span data-stu-id="fbe71-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="fbe71-108">La classe doit disposer d’un constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="fbe71-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="fbe71-109">Seuls les propriétés et les champs publics sont désérialisés.</span><span class="sxs-lookup"><span data-stu-id="fbe71-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fbe71-110">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="fbe71-110">Robust Programming</span></span>  
 <span data-ttu-id="fbe71-111">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="fbe71-111">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="fbe71-112">La classe qui est sérialisée n’a pas de constructeur public sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="fbe71-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
- <span data-ttu-id="fbe71-113">Les données du fichier ne représentent pas les données de la classe à désérialiser.</span><span class="sxs-lookup"><span data-stu-id="fbe71-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
- <span data-ttu-id="fbe71-114">Le fichier n'existe pas (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="fbe71-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fbe71-115">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fbe71-115">.NET Framework Security</span></span>  
 <span data-ttu-id="fbe71-116">Vérifiez toujours les entrées et ne désérialisez jamais les données provenant d’une source non fiable.</span><span class="sxs-lookup"><span data-stu-id="fbe71-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="fbe71-117">L’objet recréé s’exécute sur un ordinateur local avec les autorisations du code qui l’a désérialisé.</span><span class="sxs-lookup"><span data-stu-id="fbe71-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="fbe71-118">Vérifiez toutes les entrées avant d'utiliser les données dans votre application.</span><span class="sxs-lookup"><span data-stu-id="fbe71-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbe71-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbe71-119">See also</span></span>

- <xref:System.IO.StreamWriter>
- [<span data-ttu-id="fbe71-120">Guide pratique : écrire des données d’objet dans un fichier XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbe71-120">How to: Write Object Data to an XML File (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)
- [<span data-ttu-id="fbe71-121">Sérialisation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbe71-121">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="fbe71-122">Guide de programmation Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fbe71-122">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
