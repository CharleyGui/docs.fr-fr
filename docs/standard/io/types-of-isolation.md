---
title: Types d'isolation
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
ms.openlocfilehash: 9bbd2c3cdca9b2eaee268738bf99189b0be78eba
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635730"
---
# <a name="types-of-isolation"></a>Types d'isolation
L’accès au stockage isolé est toujours limité à l’utilisateur qui l’a créé. Pour implémenter ce type d’isolation, le Common Language Runtime utilise la même notion d’identité de l’utilisateur reconnue par le système d’exploitation, c’est-à-dire l’identité associée au processus par lequel le code s’exécute lorsque le magasin est ouvert. Cette identité est l’identité d’un utilisateur, mais l’emprunt d’identité peut provoquer un changement dynamique de l’identité actuelle de l’utilisateur.  
  
 L’accès au stockage isolé est également limité en fonction de l’identité associée au domaine et à l’assembly de l’application, ou à l’assembly uniquement. Le runtime obtient ces identités des façons suivantes :  
  
- L’identité de domaine constitue la preuve de l’application, et dans le cas d’une application Web, il peut s’agir de l’URL complète. Pour le code hébergé par l’interpréteur de commandes, l’identité de domaine peut être basée sur le chemin du répertoire de l’application. Par exemple, si l’exécutable s’exécute à partir du chemin d’accès C:\Office\MyApp.exe, l’identité de domaine serait C:\Office\MyApp.exe.  
  
- L’identité d’assembly est la preuve de l’assembly. Elle peut provenir d’une signature numérique chiffrée, qui peut être le [nom fort](../assembly/strong-named.md) de l’assembly, de l’éditeur du logiciel de l’assembly, ou de son identité d’URL. Si un assembly possède un nom fort et une identité d’éditeur de logiciel, l’identité de l’éditeur de logiciel est utilisée. Si l’assembly provient d’Internet et n’est pas signé, l’identité d’URL est utilisée. Pour plus d’informations sur les assemblys et les noms forts, consultez [Programmation à l'aide d'assemblys](/dotnet/standard/assembly/index).  
  
- Les magasins itinérants se déplacent avec un utilisateur qui dispose d’un profil utilisateur itinérant. Les fichiers sont enregistrés dans un répertoire réseau et téléchargés sur n’importe quel ordinateur auquel l’utilisateur se connecte. Pour plus d'informations sur les profils utilisateur itinérants, consultez <xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>.  
  
 En combinant les concepts d’utilisateur, de domaine et d’identité d’assembly, le stockage isolé permet d’isoler des données de plusieurs manières, chacune avec ses propres scénarios d’utilisation :  
  
- [Isolation par utilisateur et par assembly](#UserAssembly)  
  
- [Isolation par utilisateur, par domaine et par assembly](#UserDomainAssembly)  
  
 Chacune de ces isolations peut être combinée avec un profil utilisateur itinérant. Pour plus d’informations, consultez la section [Stockage et profil itinérant isolé](#Roaming).  
  
 L’illustration suivante montre comment les magasins sont isolés dans différentes étendues :  
  
 ![Diagramme qui montre l’isolation par utilisateur et par assembly.](./media/types-of-isolation/isolated-storage-types.gif)  
  
 À l’exception des magasins d’itinérance, le stockage isolé est toujours implicitement isolé par ordinateur parce qu’il utilise les installations de stockage qui sont locales à un ordinateur donné.  
  
> [!IMPORTANT]
> Le stockage isolé n’est pas disponible pour les applications Windows 8.x Store. À la place, utilisez les classes de données d’application des espaces de noms `Windows.Storage` inclus dans l’API Windows Runtime pour stocker des données locales et des fichiers. Pour plus d’informations, consultez [Données d’applications](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) dans le Centre de développement Windows.  
  
<a name="UserAssembly"></a>
## <a name="isolation-by-user-and-assembly"></a>Isolation par utilisateur et par assembly  
 Lorsque l’assembly qui utilise les données du magasin doit être accessible depuis n’importe quel domaine d’application, l’isolation par utilisateur et par assembly est recommandée. Dans ce cas, le stockage isolé sert généralement à stocker les données qui s’appliquent à plusieurs applications et qui ne sont pas liées à une application spécifique, par exemple le nom d’utilisateur ou des informations de licence. Pour accéder au stockage isolé par utilisateur et par assembly, le code doit être approuvé pour transférer des informations entre les applications. En règle générale, l’isolation par utilisateur et par assembly est autorisée sur les intranets mais pas sur Internet. L’appel de la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType> et le passage d’un utilisateur et d’un assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> génèrent un stockage avec ce type d’isolation.  
  
 L’exemple de code suivant extrait un magasin isolé par utilisateur et par assembly. Le magasin est accessible via l’objet `isoFile`.  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 Pour obtenir un exemple qui utilise les paramètres de preuve, consultez <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>.  
  
 La méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> est disponible comme raccourci, comme illustré dans l’exemple de code suivant. Ce raccourci ne peut pas être utilisé pour ouvrir des magasins capables d’itinérance ; utilisez <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> dans ce cas.  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>
## <a name="isolation-by-user-domain-and-assembly"></a>Isolation par utilisateur, par domaine et par assembly  
 Si votre application utilise un assembly tiers qui nécessite une banque de données privée, vous pouvez utiliser le stockage isolé pour stocker ces données privées. L’isolation par utilisateur, domaine et assembly garantit que seul le code d’un assembly donné peut accéder aux données et uniquement lorsque cet assembly est utilisé par l’application en cours d’exécution lors de la création du magasin, et lorsque l’utilisateur pour lequel le magasin a été créé exécute l’application. L’isolation par utilisateur, domaine et assembly empêche l’assembly tiers de transmettre des données à d’autres applications. Ce type d’isolation devrait être votre choix par défaut si vous savez que vous utiliserez le stockage isolé, mais que vous hésitez sur le type d’isolation adéquat. L’appel de la méthode statique <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> de <xref:System.IO.IsolatedStorage.IsolatedStorageFile> et le passage d’un utilisateur, d’un domaine et d’un assembly <xref:System.IO.IsolatedStorage.IsolatedStorageScope> génèrent un stockage avec ce type d’isolation.  
  
 L’exemple de code suivant extrait un magasin isolé par utilisateur, domaine et assembly. Le magasin est accessible via l’objet `isoFile`.  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 Une autre méthode est disponible comme raccourci, comme illustré dans l’exemple de code suivant. Ce raccourci ne peut pas être utilisé pour ouvrir des magasins capables d’itinérance ; utilisez <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> dans ce cas.  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>
## <a name="isolated-storage-and-roaming"></a>Stockage et profil itinérant isolé  
 Les profils utilisateur itinérants représentent une fonctionnalité Windows qui permet à un utilisateur de configurer une identité sur un réseau et d’utiliser cette identité pour se connecter à n’importe quel ordinateur du réseau, en conservant tous les réglages personnalisés. Un assembly qui utilise le stockage isolé peut spécifier que le stockage isolé de l’utilisateur devra accompagner le profil utilisateur itinérant. L’itinérance peut être utilisée conjointement avec l’isolation par utilisateur et par assembly, ou avec l’isolation par utilisateur, domaine et assembly. Si aucune portée d’itinérance n’est définie, les magasins ne bénéficieront d’aucune itinérance, même si un profil utilisateur itinérant est utilisé.  
  
 L’exemple de code suivant récupère un magasin itinérant isolé par utilisateur et assembly. Le magasin est accessible via l’objet `isoFile`.  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 Une portée de domaine peut être ajoutée afin de créer un magasin itinérant isolé par utilisateur, domaine et application. L'exemple de code suivant illustre cette tâche.  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.IO.IsolatedStorage.IsolatedStorageScope>
- [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
