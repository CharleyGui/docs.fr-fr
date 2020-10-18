---
title: Type '<typename>' non défini
ms.date: 07/20/2015
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
ms.openlocfilehash: 195e749e29494d438dbd052e8e308250f4cce1ca
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161892"
---
# <a name="bc30002-type-typename-is-not-defined"></a><span data-ttu-id="b3fb2-102">BC30002 : le type' \<typename> 'n’est pas défini</span><span class="sxs-lookup"><span data-stu-id="b3fb2-102">BC30002: Type '\<typename>' is not defined</span></span>

<span data-ttu-id="b3fb2-103">L’instruction a fait référence à un type qui n’a pas été défini.</span><span class="sxs-lookup"><span data-stu-id="b3fb2-103">The statement has made reference to a type that has not been defined.</span></span> <span data-ttu-id="b3fb2-104">Vous pouvez définir un type dans une instruction de déclaration comme `Enum` , `Structure` , `Class` ou `Interface` .</span><span class="sxs-lookup"><span data-stu-id="b3fb2-104">You can define a type in a declaration statement such as `Enum`, `Structure`, `Class`, or `Interface`.</span></span>

 <span data-ttu-id="b3fb2-105">**ID d’erreur :** BC30002</span><span class="sxs-lookup"><span data-stu-id="b3fb2-105">**Error ID:** BC30002</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="b3fb2-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b3fb2-106">To correct this error</span></span>

- <span data-ttu-id="b3fb2-107">Vérifiez que la définition de type et sa référence utilisent toutes les deux la même orthographe.</span><span class="sxs-lookup"><span data-stu-id="b3fb2-107">Ensure that the type definition and its reference both use the same spelling.</span></span>

- <span data-ttu-id="b3fb2-108">Assurez-vous que la définition de type est accessible à la référence.</span><span class="sxs-lookup"><span data-stu-id="b3fb2-108">Ensure that the type definition is accessible to the reference.</span></span> <span data-ttu-id="b3fb2-109">Par exemple, si le type se trouve dans un autre module et a été déclaré `Private` , déplacez la définition du type vers le module de référence ou déclarez-le `Public` .</span><span class="sxs-lookup"><span data-stu-id="b3fb2-109">For example, if the type is in another module and has been declared `Private`, move the type definition to the referencing module or declare it `Public`.</span></span>

- <span data-ttu-id="b3fb2-110">Assurez-vous que l’espace de noms du type n’est pas redéfini dans votre projet.</span><span class="sxs-lookup"><span data-stu-id="b3fb2-110">Ensure that the namespace of the type is not redefined within your project.</span></span> <span data-ttu-id="b3fb2-111">Si c’est le cas, utilisez le `Global` mot clé pour qualifier complètement le nom de type.</span><span class="sxs-lookup"><span data-stu-id="b3fb2-111">If it is, use the `Global` keyword to fully qualify the type name.</span></span> <span data-ttu-id="b3fb2-112">Par exemple, si un projet définit un espace de noms nommé `System` , le <xref:System.Object?displayProperty=nameWithType> type n’est pas accessible, sauf s’il est qualifié complet avec le `Global` mot clé : `Global.System.Object` .</span><span class="sxs-lookup"><span data-stu-id="b3fb2-112">For example, if a project defines a namespace named `System`, the <xref:System.Object?displayProperty=nameWithType> type cannot be accessed unless it is fully qualified with the `Global` keyword: `Global.System.Object`.</span></span>

- <span data-ttu-id="b3fb2-113">Si le type est défini, mais que la bibliothèque d’objets ou la bibliothèque de types dans laquelle il est défini n’est pas inscrite dans Visual Basic, cliquez sur **Ajouter une référence** dans le menu **projet** , puis sélectionnez la bibliothèque d’objets ou la bibliothèque de types appropriée.</span><span class="sxs-lookup"><span data-stu-id="b3fb2-113">If the type is defined, but the object library or type library in which it is defined is not registered in Visual Basic, click **Add Reference** on the **Project** menu, and then select the appropriate object library or type library.</span></span>

- <span data-ttu-id="b3fb2-114">Assurez-vous que le type se trouve dans un assembly qui fait partie du profil de .NET Framework ciblé.</span><span class="sxs-lookup"><span data-stu-id="b3fb2-114">Ensure that the type is in an assembly that is part of the targeted .NET Framework profile.</span></span> <span data-ttu-id="b3fb2-115">Pour plus d’informations, consultez [Dépannage des erreurs de ciblage du .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span><span class="sxs-lookup"><span data-stu-id="b3fb2-115">For more information, see [Troubleshooting .NET Framework Targeting Errors](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).</span></span>

## <a name="see-also"></a><span data-ttu-id="b3fb2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b3fb2-116">See also</span></span>

- [<span data-ttu-id="b3fb2-117">Espaces de noms dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3fb2-117">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="b3fb2-118">Enum (instruction)</span><span class="sxs-lookup"><span data-stu-id="b3fb2-118">Enum Statement</span></span>](../statements/enum-statement.md)
- [<span data-ttu-id="b3fb2-119">Structure, instruction</span><span class="sxs-lookup"><span data-stu-id="b3fb2-119">Structure Statement</span></span>](../statements/structure-statement.md)
- [<span data-ttu-id="b3fb2-120">Class (instruction)</span><span class="sxs-lookup"><span data-stu-id="b3fb2-120">Class Statement</span></span>](../statements/class-statement.md)
- [<span data-ttu-id="b3fb2-121">Interface (instruction)</span><span class="sxs-lookup"><span data-stu-id="b3fb2-121">Interface Statement</span></span>](../statements/interface-statement.md)
- [<span data-ttu-id="b3fb2-122">Gestion des références dans un projet</span><span class="sxs-lookup"><span data-stu-id="b3fb2-122">Managing references in a project</span></span>](/visualstudio/ide/managing-references-in-a-project)
