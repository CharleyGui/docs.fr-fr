---
title: Copie et mise à jour des expressions d’enregistrement
description: Découvrez comment écrire une «copie et une expression de mise à jour» qui copie un enregistrement ou un enregistrement anonyme existant, met à jour les champs spécifiés et retourne l’enregistrement ou l’enregistrement anonyme mis à jour.
author: ChrSteinert
ms.date: 06/12/2019
ms.openlocfilehash: dfb20a6ff8282ae5988772cc0f0841db23aad942
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630381"
---
# <a name="copy-and-update-record-expressions"></a><span data-ttu-id="ea8d6-103">Copie et mise à jour des expressions d’enregistrement</span><span class="sxs-lookup"><span data-stu-id="ea8d6-103">Copy and Update Record Expressions</span></span>

<span data-ttu-id="ea8d6-104">Une *expression d’enregistrement de copie et de mise à jour* est une expression qui copie un enregistrement existant, met à jour les champs spécifiés et retourne l’enregistrement mis à jour.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-104">A *copy and update record expression* is an expression that copies an existing record, updates specified fields, and returns the updated record.</span></span>

## <a name="syntax"></a><span data-ttu-id="ea8d6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea8d6-105">Syntax</span></span>

```fsharp
{ record-name with
    updated-labels }

{| anonymous-record-name with
    updated-labels |}
```

## <a name="remarks"></a><span data-ttu-id="ea8d6-106">Notes</span><span class="sxs-lookup"><span data-stu-id="ea8d6-106">Remarks</span></span>

<span data-ttu-id="ea8d6-107">Par défaut, les enregistrements et les enregistrements anonymes sont immuables, ce qui signifie qu’il n’existe pas de mise à jour d’un enregistrement existant.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-107">Records and anonymous records are immutable by default, so that there is no update to an existing record possible.</span></span> <span data-ttu-id="ea8d6-108">Pour créer un enregistrement mis à jour, tous les champs d’un enregistrement doivent être spécifiés à nouveau.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-108">To create an updated record all the fields of a record would have to be specified again.</span></span> <span data-ttu-id="ea8d6-109">Pour simplifier cette tâche, vous pouvez utiliser une *expression de copie et de mise à jour* .</span><span class="sxs-lookup"><span data-stu-id="ea8d6-109">To simplify this task a *copy and update expression* can be used.</span></span> <span data-ttu-id="ea8d6-110">Cette expression prend un enregistrement existant, crée un nouveau du même type en utilisant les champs spécifiés de l’expression et le champ manquant spécifié par l’expression.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-110">This expression takes an existing record, creates a new one of the same type by using specified fields from the expression and the missing field specified by the expression.</span></span>

<span data-ttu-id="ea8d6-111">Cela peut être utile lorsque vous devez copier un enregistrement existant et éventuellement modifier certaines valeurs de champ.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-111">This can be useful when you have to copy an existing record, and possibly change some of the field values.</span></span>

<span data-ttu-id="ea8d6-112">Prenons l’exemple d’un enregistrement nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="ea8d6-112">Take for instance a newly created record.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1905.fs)]

<span data-ttu-id="ea8d6-113">Si vous mettez à jour uniquement le champ de cet enregistrement, vous pouvez utiliser l' *expression d’enregistrement copier et mettre à jour* comme suit:</span><span class="sxs-lookup"><span data-stu-id="ea8d6-113">If you were to update only on field of that record you could use the *copy and update record expression* like the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1906.fs)]

## <a name="see-also"></a><span data-ttu-id="ea8d6-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea8d6-114">See also</span></span>

- [<span data-ttu-id="ea8d6-115">Enregistrements</span><span class="sxs-lookup"><span data-stu-id="ea8d6-115">Records</span></span>](records.md)
- [<span data-ttu-id="ea8d6-116">Enregistrements anonymes</span><span class="sxs-lookup"><span data-stu-id="ea8d6-116">Anonymous Records</span></span>](anonymous-records.md)
- [<span data-ttu-id="ea8d6-117">Informations de référence du langage F#</span><span class="sxs-lookup"><span data-stu-id="ea8d6-117">F# Language Reference</span></span>](index.md)
