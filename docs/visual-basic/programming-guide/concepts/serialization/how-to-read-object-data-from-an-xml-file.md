---
title: 'Comment : lire des données d’objet à partir d’un fichier XML'
ms.date: 07/20/2015
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
ms.openlocfilehash: 7677b32f76bee3fe579f96715b6c748c08c83a82
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077239"
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>Guide pratique : lire des données d’objet à partir d’un fichier XML (Visual Basic)

Cet exemple lit des données d’objet écrites précédemment dans un fichier XML en utilisant la classe <xref:System.Xml.Serialization.XmlSerializer>.  
  
## <a name="example"></a>Exemple  
  
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
  
## <a name="compile-the-code"></a>Compiler le code  

 Remplacez le nom du fichier « c:\temp\SerializationOverview.xml » par le nom du fichier qui contient les données sérialisées. Pour plus d’informations sur la sérialisation des données, consultez [Comment : écrire des données d’objet dans un fichier XML (Visual Basic)](how-to-write-object-data-to-an-xml-file.md).  
  
 La classe doit disposer d’un constructeur public sans paramètres.  
  
 Seuls les propriétés et les champs publics sont désérialisés.  
  
## <a name="robust-programming"></a>Programmation fiable  

 Les conditions ci-dessous peuvent générer une exception.  
  
- La classe qui est sérialisée n’a pas de constructeur public sans paramètres.  
  
- Les données du fichier ne représentent pas les données de la classe à désérialiser.  
  
- Le fichier n'existe pas (<xref:System.IO.IOException>).  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  

 Vérifiez toujours les entrées et ne désérialisez jamais les données provenant d’une source non fiable. L’objet recréé s’exécute sur un ordinateur local avec les autorisations du code qui l’a désérialisé. Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.StreamWriter>
- [Guide pratique : écrire des données d’objet dans un fichier XML (Visual Basic)](how-to-write-object-data-to-an-xml-file.md)
- [Sérialisation (Visual Basic)](index.md)
- [Guide de programmation Visual Basic](../../index.md)
