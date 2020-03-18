---
title: '##pragma checksum - Référence C#'
ms.date: 07/20/2015
f1_keywords:
- '#pragma checksum'
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
ms.openlocfilehash: 1bbb404e1183daa5e68e512e7439b6ae52abd605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712479"
---
# <a name="pragma-checksum-c-reference"></a>#pragma checksum (Référence C#)
Génère des sommes de contrôle pour les fichiers sources afin de faciliter le débogage des pages ASP.NET.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
## <a name="parameters"></a>Paramètres  
 `"filename"`  
 Nom du fichier dont les modifications ou les mises à jour doivent faire l’objet d’une surveillance.  
  
 `"{guid}"`  
 Identificateur global unique (GUID) du fichier pour l’algorithme de hachage.  
  
 `"checksum_bytes"`  
 Chaîne de chiffres hexadécimaux représentant les octets de la somme de contrôle. Doit être un nombre pair de chiffres hexadécimaux. S’il y a un nombre impair de chiffres, un avertissement est généré au moment de la compilation et la directive est ignorée.  
  
## <a name="remarks"></a>Notes   
 Le débogueur Visual Studio utilise une somme de contrôle pour s’assurer de toujours trouver la bonne source. Le compilateur calcule la somme de contrôle pour un fichier source, puis envoie la sortie vers le fichier de base de données du programme (PDB). Le débogueur utilise ensuite le fichier PDB à comparer avec la somme de contrôle qu’il calcule pour le fichier source.  
  
 Cette solution ne fonctionne pas pour les projets ASP.NET, car la somme de contrôle est calculée pour le fichier source généré, au lieu du fichier .aspx. Pour résoudre ce problème, `#pragma checksum` fournit une prise en charge de la somme de contrôle pour les pages ASP.NET.  
  
 Quand vous créez un projet ASP.NET dans Visual C#, le fichier source généré contient une somme de contrôle pour le fichier .aspx, à partir duquel la source est générée. Le compilateur écrit ensuite ces informations dans le fichier PDB.  
  
 Si le compilateur ne rencontre aucune directive `#pragma checksum` dans le fichier, il calcule la somme de contrôle et écrit la valeur dans le fichier PDB.  
  
## <a name="example"></a> Exemple  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{406EA660-64CF-4C82-B6F0-42D48172A799}" "ab007f1d23d9" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Référence C](../index.md)
- [Guide de programmation C#](../../programming-guide/index.md)
- [Directives de préprocesseur de CMD](./index.md)
