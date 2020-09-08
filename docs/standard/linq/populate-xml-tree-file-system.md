---
title: Comment remplir une arborescence XML à partir du système de fichiers-LINQ to XML
description: Découvrez comment remplir une arborescence XML à partir du système de fichiers en C# ou Visual Basic.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2aa2ccac-4a22-47ae-9107-3bb8df232576
ms.openlocfilehash: 6b0307aca9c9075120021967c08efcad8b595653
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89553725"
---
# <a name="how-to-populate-an-xml-tree-from-the-file-system-linq-to-xml"></a><span data-ttu-id="c3481-103">Comment remplir une arborescence XML à partir du système de fichiers (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c3481-103">How to populate an XML tree from the file system (LINQ to XML)</span></span>

<span data-ttu-id="c3481-104">Une application courante et utile des arborescences XML est comme un magasin de données de valeur de nom hiérarchique.</span><span class="sxs-lookup"><span data-stu-id="c3481-104">A common and useful application of XML trees is as a hierarchical name-value data store.</span></span> <span data-ttu-id="c3481-105">Vous pouvez remplir une arborescence XML avec des données hiérarchiques, puis les interroger, les transformer et, si nécessaire, les sérialiser.</span><span class="sxs-lookup"><span data-stu-id="c3481-105">You can populate an XML tree with hierarchical data, and then query it, transform it, and if necessary, serialize it.</span></span> <span data-ttu-id="c3481-106">Pour ce faire, une grande partie de la sémantique spécifique à XML, telle que les espaces de noms et le comportement d’espace blanc, n’est pas importante.</span><span class="sxs-lookup"><span data-stu-id="c3481-106">For this use, many of the XML-specific semantics, such as namespaces and white space behavior, aren't important.</span></span> <span data-ttu-id="c3481-107">Au lieu de cela, vous utilisez l’arborescence XML en tant que base de données hiérarchique de petite taille, en mémoire et à utilisateur unique.</span><span class="sxs-lookup"><span data-stu-id="c3481-107">Instead, you're using the XML tree as a small, in-memory, single-user hierarchical database.</span></span>

## <a name="example-populate-an-xml-tree-and-then-query-it"></a><span data-ttu-id="c3481-108">Exemple : remplir une arborescence XML et l’interroger</span><span class="sxs-lookup"><span data-stu-id="c3481-108">Example: Populate an XML tree and then query it</span></span>

<span data-ttu-id="c3481-109">L’exemple suivant utilise la récursivité pour remplir une arborescence XML avec des données relatives aux fichiers dans le système de fichiers local.</span><span class="sxs-lookup"><span data-stu-id="c3481-109">The following example uses recursion to populate an XML tree with data about the files in the local file system.</span></span> <span data-ttu-id="c3481-110">Il interroge ensuite l’arborescence, en totalisant toutes les tailles de fichier.</span><span class="sxs-lookup"><span data-stu-id="c3481-110">It then queries the tree, totalling all the file sizes.</span></span>

```csharp
class Program
{
    static XElement CreateFileSystemXmlTree(string source)
    {
        DirectoryInfo di = new DirectoryInfo(source);
        return new XElement("Dir",
            new XAttribute("Name", di.Name),
            from d in Directory.GetDirectories(source)
            select CreateFileSystemXmlTree(d),
            from fi in di.GetFiles()
            select new XElement("File",
                new XElement("Name", fi.Name),
                new XElement("Length", fi.Length)
            )
        );
    }

    static void Main(string[] args)
    {
        XElement fileSystemTree = CreateFileSystemXmlTree("C:/Tmp");
        Console.WriteLine(fileSystemTree);
        Console.WriteLine("------");
        long totalFileSize =
            (from f in fileSystemTree.Descendants("File")
             select (long)f.Element("Length")).Sum();
        Console.WriteLine("Total File Size:{0}", totalFileSize);
    }
}
```

```vb
Module Module1
    Function CreateFileSystemXmlTree(ByVal source As String) As XElement
        Dim di As DirectoryInfo = New DirectoryInfo(source)
        Return <Dir Name=<%= di.Name %>>
                   <%= From d In Directory.GetDirectories(source) _
                       Select CreateFileSystemXmlTree(d) %>
                   <%= From fi In di.GetFiles() _
                       Select <File>
                                  <Name><%= fi.Name %></Name>
                                  <Length><%= fi.Length %></Length>
                              </File> %>
               </Dir>
    End Function

    Sub Main()
        Dim fileSystemTree As XElement = CreateFileSystemXmlTree("C:/Tmp")
        Console.WriteLine(fileSystemTree)
        Console.WriteLine("------")
        Dim totalFileSize As Long = _
            ( _
                From f In fileSystemTree...<File> _
                Select CLng(f.<Length>(0)) _
            ).Sum()
        Console.WriteLine("Total File Size:{0}", totalFileSize)
    End Sub
End Module
```

<span data-ttu-id="c3481-111">L’exemple produit une sortie similaire à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c3481-111">The example produces output similar to the following:</span></span>

```xml
<Dir Name="Tmp">
  <Dir Name="ConsoleApplication1">
    <Dir Name="bin">
      <Dir Name="Debug">
        <File>
          <Name>ConsoleApplication1.exe</Name>
          <Length>4608</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.pdb</Name>
          <Length>11776</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.vshost.exe</Name>
          <Length>9568</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.vshost.exe.manifest</Name>
          <Length>473</Length>
        </File>
      </Dir>
    </Dir>
    <Dir Name="obj">
      <Dir Name="Debug">
        <Dir Name="TempPE" />
        <File>
          <Name>ConsoleApplication1.csproj.FileListAbsolute.txt</Name>
          <Length>322</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.exe</Name>
          <Length>4608</Length>
        </File>
        <File>
          <Name>ConsoleApplication1.pdb</Name>
          <Length>11776</Length>
        </File>
      </Dir>
    </Dir>
    <Dir Name="Properties">
      <File>
        <Name>AssemblyInfo.cs</Name>
        <Length>1454</Length>
      </File>
    </Dir>
    <File>
      <Name>ConsoleApplication1.csproj</Name>
      <Length>2546</Length>
    </File>
    <File>
      <Name>ConsoleApplication1.sln</Name>
      <Length>937</Length>
    </File>
    <File>
      <Name>ConsoleApplication1.suo</Name>
      <Length>10752</Length>
    </File>
    <File>
      <Name>Program.cs</Name>
      <Length>269</Length>
    </File>
  </Dir>
</Dir>
------
Total File Size:59089
```
