---
title: Copie et mise à jour des expressions d’enregistrement
description: Découvrez comment écrire une « expression de copie et mise à jour » qui copie un enregistrement existant ou un enregistrement anonyme, met à jour les champs spécifiés et renvoie l’enregistrement mis à jour ou l’enregistrement anonyme.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: bec3e0ac2fb34e358b199c509c4599b55d7bf35e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739284"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="50183-103">Copie et mise à jour des expressions d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="50183-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="50183-104">Une *expression d’enregistrement de copie et de mise à jour* est une expression qui copie un enregistrement existant, met à jour les champs spécifiés et renvoie l’enregistrement mis à jour.</span><span class="sxs-lookup"><span data-stu-id="50183-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="50183-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50183-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="50183-106">Notes</span><span class="sxs-lookup"><span data-stu-id="50183-106">Remarks</span></span>

<span data-ttu-id="50183-107">Les enregistrements et les enregistrements anonymes sont immuables par défaut, il n’est donc pas possible de mettre à jour un enregistrement existant.</span><span class="sxs-lookup"><span data-stu-id="50183-107">Records and anonymous records are immutable by default, so it is not possible to update an existing record.</span></span> <span data-ttu-id="50183-108">Pour créer un enregistrement mis à jour, tous les champs d’un enregistrement devraient être spécifiés à nouveau.</span><span class="sxs-lookup"><span data-stu-id="50183-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="50183-109">Pour simplifier cette tâche, une *copie et une mise à jour de l’expression* peuvent être utilisées.</span><span class="sxs-lookup"><span data-stu-id="50183-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="50183-110">Cette expression prend un enregistrement existant, crée un nouveau du même type en utilisant des champs spécifiés de l’expression et le champ manquant spécifié par l’expression.</span><span class="sxs-lookup"><span data-stu-id="50183-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="50183-111">Cela peut être utile lorsque vous devez copier un enregistrement existant, et peut-être changer certaines des valeurs de champ.</span><span class="sxs-lookup"><span data-stu-id="50183-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="50183-112">Prenez par exemple un disque nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="50183-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="50183-113">Pour mettre à jour seulement deux champs de cet enregistrement, vous pouvez utiliser la *copie et mettre à jour l’expression d’enregistrement*:</span><span class="sxs-lookup"><span data-stu-id="50183-113">To update only two fields in that record you can use the *copy and update record expression*:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="50183-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="50183-114">See also</span></span>

- [<span data-ttu-id="50183-115">Dossiers</span><span class="sxs-lookup"><span data-stu-id="50183-115">Records</span></span>](records.md)
- [<span data-ttu-id="50183-116">Enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="50183-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="50183-117">Référence linguistique F</span><span class="sxs-lookup"><span data-stu-id="50183-117">F# Language Reference</span></span>](index.md)
