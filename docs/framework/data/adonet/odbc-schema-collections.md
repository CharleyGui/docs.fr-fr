---
title: Collections de schémas ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: f0240e99d2420b0956d3c144f837b39e094bb78a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794720"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="f251e-102">Collections de schémas ODBC</span><span class="sxs-lookup"><span data-stu-id="f251e-102">ODBC Schema Collections</span></span>

<span data-ttu-id="f251e-103">Cette section traite de la prise en charge des collections de schémas pour les pilotes ODBC Microsoft SQL Server, Oracle et Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="f251e-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>

## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="f251e-104">Pilote Microsoft SQL Server ODBC</span><span class="sxs-lookup"><span data-stu-id="f251e-104">Microsoft SQL Server ODBC Driver</span></span>

<span data-ttu-id="f251e-105">Le pilote ODBC Microsoft SQL Server prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="f251e-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="f251e-106">Tables</span><span class="sxs-lookup"><span data-stu-id="f251e-106">Tables</span></span>

- <span data-ttu-id="f251e-107">Index</span><span class="sxs-lookup"><span data-stu-id="f251e-107">Indexes</span></span>

- <span data-ttu-id="f251e-108">Colonnes</span><span class="sxs-lookup"><span data-stu-id="f251e-108">Columns</span></span>

- <span data-ttu-id="f251e-109">Procédures</span><span class="sxs-lookup"><span data-stu-id="f251e-109">Procedures</span></span>

- <span data-ttu-id="f251e-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f251e-110">ProcedureColumns</span></span>

- <span data-ttu-id="f251e-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f251e-111">ProcedureParameters</span></span>

- <span data-ttu-id="f251e-112">Affichages</span><span class="sxs-lookup"><span data-stu-id="f251e-112">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="f251e-113">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="f251e-113">Tables and Views</span></span>

|<span data-ttu-id="f251e-114">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-114">ColumnName</span></span>|<span data-ttu-id="f251e-115">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-115">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f251e-116">TABLE_CAT</span></span>|<span data-ttu-id="f251e-117">String</span><span class="sxs-lookup"><span data-stu-id="f251e-117">String</span></span>|
|<span data-ttu-id="f251e-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f251e-118">TABLE_SCHEM</span></span>|<span data-ttu-id="f251e-119">String</span><span class="sxs-lookup"><span data-stu-id="f251e-119">String</span></span>|
|<span data-ttu-id="f251e-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-120">TABLE_NAME</span></span>|<span data-ttu-id="f251e-121">String</span><span class="sxs-lookup"><span data-stu-id="f251e-121">String</span></span>|
|<span data-ttu-id="f251e-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-122">TABLE_TYPE</span></span>|<span data-ttu-id="f251e-123">String</span><span class="sxs-lookup"><span data-stu-id="f251e-123">String</span></span>|
|<span data-ttu-id="f251e-124">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-124">REMARKS</span></span>|<span data-ttu-id="f251e-125">String</span><span class="sxs-lookup"><span data-stu-id="f251e-125">String</span></span>|

### <a name="indexes"></a><span data-ttu-id="f251e-126">Index</span><span class="sxs-lookup"><span data-stu-id="f251e-126">Indexes</span></span>

|<span data-ttu-id="f251e-127">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-127">ColumnName</span></span>|<span data-ttu-id="f251e-128">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-128">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f251e-129">TABLE_CAT</span></span>|<span data-ttu-id="f251e-130">String</span><span class="sxs-lookup"><span data-stu-id="f251e-130">String</span></span>|
|<span data-ttu-id="f251e-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f251e-131">TABLE_SCHEM</span></span>|<span data-ttu-id="f251e-132">String</span><span class="sxs-lookup"><span data-stu-id="f251e-132">String</span></span>|
|<span data-ttu-id="f251e-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-133">TABLE_NAME</span></span>|<span data-ttu-id="f251e-134">String</span><span class="sxs-lookup"><span data-stu-id="f251e-134">String</span></span>|
|<span data-ttu-id="f251e-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="f251e-135">NON_UNIQUE</span></span>|<span data-ttu-id="f251e-136">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-136">Int16</span></span>|
|<span data-ttu-id="f251e-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="f251e-138">String</span><span class="sxs-lookup"><span data-stu-id="f251e-138">String</span></span>|
|<span data-ttu-id="f251e-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-139">INDEX_NAME</span></span>|<span data-ttu-id="f251e-140">String</span><span class="sxs-lookup"><span data-stu-id="f251e-140">String</span></span>|
|<span data-ttu-id="f251e-141">TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-141">TYPE</span></span>|<span data-ttu-id="f251e-142">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-142">Int16</span></span>|
|<span data-ttu-id="f251e-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-144">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-144">Int16</span></span>|
|<span data-ttu-id="f251e-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-145">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-146">String</span><span class="sxs-lookup"><span data-stu-id="f251e-146">String</span></span>|
|<span data-ttu-id="f251e-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="f251e-147">ASC_OR_DESC</span></span>|<span data-ttu-id="f251e-148">String</span><span class="sxs-lookup"><span data-stu-id="f251e-148">String</span></span>|
|<span data-ttu-id="f251e-149">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="f251e-149">CARDINALITY</span></span>|<span data-ttu-id="f251e-150">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-150">Int32</span></span>|
|<span data-ttu-id="f251e-151">PAGES</span><span class="sxs-lookup"><span data-stu-id="f251e-151">PAGES</span></span>|<span data-ttu-id="f251e-152">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-152">Int32</span></span>|
|<span data-ttu-id="f251e-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="f251e-153">FILTER_CONDITION</span></span>|<span data-ttu-id="f251e-154">String</span><span class="sxs-lookup"><span data-stu-id="f251e-154">String</span></span>|
|<span data-ttu-id="f251e-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f251e-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f251e-156">String</span><span class="sxs-lookup"><span data-stu-id="f251e-156">String</span></span>|
|<span data-ttu-id="f251e-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="f251e-158">Byte</span><span class="sxs-lookup"><span data-stu-id="f251e-158">Byte</span></span>|

### <a name="columns"></a><span data-ttu-id="f251e-159">Colonnes</span><span class="sxs-lookup"><span data-stu-id="f251e-159">Columns</span></span>

|<span data-ttu-id="f251e-160">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-160">ColumnName</span></span>|<span data-ttu-id="f251e-161">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-161">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="f251e-162">TABLE_CAT</span></span>|<span data-ttu-id="f251e-163">String</span><span class="sxs-lookup"><span data-stu-id="f251e-163">String</span></span>|
|<span data-ttu-id="f251e-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f251e-164">TABLE_SCHEM</span></span>|<span data-ttu-id="f251e-165">String</span><span class="sxs-lookup"><span data-stu-id="f251e-165">String</span></span>|
|<span data-ttu-id="f251e-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-166">TABLE_NAME</span></span>|<span data-ttu-id="f251e-167">String</span><span class="sxs-lookup"><span data-stu-id="f251e-167">String</span></span>|
|<span data-ttu-id="f251e-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-168">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-169">String</span><span class="sxs-lookup"><span data-stu-id="f251e-169">String</span></span>|
|<span data-ttu-id="f251e-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-170">DATA_TYPE</span></span>|<span data-ttu-id="f251e-171">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-171">Int16</span></span>|
|<span data-ttu-id="f251e-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-172">TYPE_NAME</span></span>|<span data-ttu-id="f251e-173">String</span><span class="sxs-lookup"><span data-stu-id="f251e-173">String</span></span>|
|<span data-ttu-id="f251e-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f251e-174">COLUMN_SIZE</span></span>|<span data-ttu-id="f251e-175">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-175">Int32</span></span>|
|<span data-ttu-id="f251e-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="f251e-177">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-177">Int32</span></span>|
|<span data-ttu-id="f251e-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f251e-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f251e-179">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-179">Int16</span></span>|
|<span data-ttu-id="f251e-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f251e-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f251e-181">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-181">Int16</span></span>|
|<span data-ttu-id="f251e-182">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-182">NULLABLE</span></span>|<span data-ttu-id="f251e-183">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-183">Int16</span></span>|
|<span data-ttu-id="f251e-184">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-184">REMARKS</span></span>|<span data-ttu-id="f251e-185">String</span><span class="sxs-lookup"><span data-stu-id="f251e-185">String</span></span>|
|<span data-ttu-id="f251e-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f251e-186">COLUMN_DEF</span></span>|<span data-ttu-id="f251e-187">String</span><span class="sxs-lookup"><span data-stu-id="f251e-187">String</span></span>|
|<span data-ttu-id="f251e-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f251e-189">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-189">Int16</span></span>|
|<span data-ttu-id="f251e-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f251e-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f251e-191">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-191">Int16</span></span>|
|<span data-ttu-id="f251e-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f251e-193">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-193">Int32</span></span>|
|<span data-ttu-id="f251e-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-195">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-195">Int32</span></span>|
|<span data-ttu-id="f251e-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-196">IS_NULLABLE</span></span>|<span data-ttu-id="f251e-197">String</span><span class="sxs-lookup"><span data-stu-id="f251e-197">String</span></span>|
|<span data-ttu-id="f251e-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f251e-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f251e-199">String</span><span class="sxs-lookup"><span data-stu-id="f251e-199">String</span></span>|
|<span data-ttu-id="f251e-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f251e-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f251e-201">String</span><span class="sxs-lookup"><span data-stu-id="f251e-201">String</span></span>|
|<span data-ttu-id="f251e-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="f251e-203">Byte</span><span class="sxs-lookup"><span data-stu-id="f251e-203">Byte</span></span>|

### <a name="procedures"></a><span data-ttu-id="f251e-204">Procédures</span><span class="sxs-lookup"><span data-stu-id="f251e-204">Procedures</span></span>

|<span data-ttu-id="f251e-205">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-205">ColumnName</span></span>|<span data-ttu-id="f251e-206">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-206">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f251e-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="f251e-208">String</span><span class="sxs-lookup"><span data-stu-id="f251e-208">String</span></span>|
|<span data-ttu-id="f251e-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f251e-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f251e-210">String</span><span class="sxs-lookup"><span data-stu-id="f251e-210">String</span></span>|
|<span data-ttu-id="f251e-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="f251e-212">String</span><span class="sxs-lookup"><span data-stu-id="f251e-212">String</span></span>|
|<span data-ttu-id="f251e-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f251e-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f251e-214">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-214">Int32</span></span>|
|<span data-ttu-id="f251e-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f251e-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f251e-216">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-216">Int32</span></span>|
|<span data-ttu-id="f251e-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f251e-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f251e-218">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-218">Int32</span></span>|
|<span data-ttu-id="f251e-219">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-219">REMARKS</span></span>|<span data-ttu-id="f251e-220">String</span><span class="sxs-lookup"><span data-stu-id="f251e-220">String</span></span>|
|<span data-ttu-id="f251e-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f251e-222">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-222">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="f251e-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f251e-223">ProcedureColumns</span></span>

|<span data-ttu-id="f251e-224">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-224">ColumnName</span></span>|<span data-ttu-id="f251e-225">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-225">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f251e-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="f251e-227">String</span><span class="sxs-lookup"><span data-stu-id="f251e-227">String</span></span>|
|<span data-ttu-id="f251e-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f251e-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f251e-229">String</span><span class="sxs-lookup"><span data-stu-id="f251e-229">String</span></span>|
|<span data-ttu-id="f251e-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="f251e-231">String</span><span class="sxs-lookup"><span data-stu-id="f251e-231">String</span></span>|
|<span data-ttu-id="f251e-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-232">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-233">String</span><span class="sxs-lookup"><span data-stu-id="f251e-233">String</span></span>|
|<span data-ttu-id="f251e-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-234">COLUMN_TYPE</span></span>|<span data-ttu-id="f251e-235">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-235">Int16</span></span>|
|<span data-ttu-id="f251e-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-236">DATA_TYPE</span></span>|<span data-ttu-id="f251e-237">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-237">Int16</span></span>|
|<span data-ttu-id="f251e-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-238">TYPE_NAME</span></span>|<span data-ttu-id="f251e-239">String</span><span class="sxs-lookup"><span data-stu-id="f251e-239">String</span></span>|
|<span data-ttu-id="f251e-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f251e-240">COLUMN_SIZE</span></span>|<span data-ttu-id="f251e-241">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-241">Int32</span></span>|
|<span data-ttu-id="f251e-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="f251e-243">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-243">Int32</span></span>|
|<span data-ttu-id="f251e-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f251e-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f251e-245">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-245">Int16</span></span>|
|<span data-ttu-id="f251e-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f251e-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f251e-247">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-247">Int16</span></span>|
|<span data-ttu-id="f251e-248">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-248">NULLABLE</span></span>|<span data-ttu-id="f251e-249">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-249">Int16</span></span>|
|<span data-ttu-id="f251e-250">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-250">REMARKS</span></span>|<span data-ttu-id="f251e-251">String</span><span class="sxs-lookup"><span data-stu-id="f251e-251">String</span></span>|
|<span data-ttu-id="f251e-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f251e-252">COLUMN_DEF</span></span>|<span data-ttu-id="f251e-253">String</span><span class="sxs-lookup"><span data-stu-id="f251e-253">String</span></span>|
|<span data-ttu-id="f251e-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f251e-255">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-255">Int16</span></span>|
|<span data-ttu-id="f251e-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f251e-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f251e-257">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-257">Int16</span></span>|
|<span data-ttu-id="f251e-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f251e-259">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-259">Int32</span></span>|
|<span data-ttu-id="f251e-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-261">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-261">Int32</span></span>|
|<span data-ttu-id="f251e-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-262">IS_NULLABLE</span></span>|<span data-ttu-id="f251e-263">String</span><span class="sxs-lookup"><span data-stu-id="f251e-263">String</span></span>|
|<span data-ttu-id="f251e-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f251e-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f251e-265">String</span><span class="sxs-lookup"><span data-stu-id="f251e-265">String</span></span>|
|<span data-ttu-id="f251e-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f251e-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f251e-267">String</span><span class="sxs-lookup"><span data-stu-id="f251e-267">String</span></span>|
|<span data-ttu-id="f251e-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="f251e-269">Byte</span><span class="sxs-lookup"><span data-stu-id="f251e-269">Byte</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="f251e-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f251e-270">ProcedureParameters</span></span>

|<span data-ttu-id="f251e-271">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-271">ColumnName</span></span>|<span data-ttu-id="f251e-272">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-272">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f251e-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="f251e-274">String</span><span class="sxs-lookup"><span data-stu-id="f251e-274">String</span></span>|
|<span data-ttu-id="f251e-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f251e-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f251e-276">String</span><span class="sxs-lookup"><span data-stu-id="f251e-276">String</span></span>|
|<span data-ttu-id="f251e-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="f251e-278">String</span><span class="sxs-lookup"><span data-stu-id="f251e-278">String</span></span>|
|<span data-ttu-id="f251e-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-279">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-280">String</span><span class="sxs-lookup"><span data-stu-id="f251e-280">String</span></span>|
|<span data-ttu-id="f251e-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-281">COLUMN_TYPE</span></span>|<span data-ttu-id="f251e-282">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-282">Int16</span></span>|
|<span data-ttu-id="f251e-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-283">DATA_TYPE</span></span>|<span data-ttu-id="f251e-284">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-284">Int16</span></span>|
|<span data-ttu-id="f251e-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-285">TYPE_NAME</span></span>|<span data-ttu-id="f251e-286">String</span><span class="sxs-lookup"><span data-stu-id="f251e-286">String</span></span>|
|<span data-ttu-id="f251e-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f251e-287">COLUMN_SIZE</span></span>|<span data-ttu-id="f251e-288">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-288">Int32</span></span>|
|<span data-ttu-id="f251e-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="f251e-290">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-290">Int32</span></span>|
|<span data-ttu-id="f251e-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f251e-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f251e-292">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-292">Int16</span></span>|
|<span data-ttu-id="f251e-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f251e-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f251e-294">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-294">Int16</span></span>|
|<span data-ttu-id="f251e-295">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-295">NULLABLE</span></span>|<span data-ttu-id="f251e-296">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-296">Int16</span></span>|
|<span data-ttu-id="f251e-297">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-297">REMARKS</span></span>|<span data-ttu-id="f251e-298">String</span><span class="sxs-lookup"><span data-stu-id="f251e-298">String</span></span>|
|<span data-ttu-id="f251e-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f251e-299">COLUMN_DEF</span></span>|<span data-ttu-id="f251e-300">String</span><span class="sxs-lookup"><span data-stu-id="f251e-300">String</span></span>|
|<span data-ttu-id="f251e-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f251e-302">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-302">Int16</span></span>|
|<span data-ttu-id="f251e-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f251e-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f251e-304">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-304">Int16</span></span>|
|<span data-ttu-id="f251e-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f251e-306">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-306">Int32</span></span>|
|<span data-ttu-id="f251e-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-308">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-308">Int32</span></span>|
|<span data-ttu-id="f251e-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-309">IS_NULLABLE</span></span>|<span data-ttu-id="f251e-310">String</span><span class="sxs-lookup"><span data-stu-id="f251e-310">String</span></span>|
|<span data-ttu-id="f251e-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="f251e-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="f251e-312">String</span><span class="sxs-lookup"><span data-stu-id="f251e-312">String</span></span>|
|<span data-ttu-id="f251e-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="f251e-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="f251e-314">String</span><span class="sxs-lookup"><span data-stu-id="f251e-314">String</span></span>|
|<span data-ttu-id="f251e-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="f251e-316">Byte</span><span class="sxs-lookup"><span data-stu-id="f251e-316">Byte</span></span>|

## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="f251e-317">Pilote Microsoft Oracle ODBC</span><span class="sxs-lookup"><span data-stu-id="f251e-317">Microsoft Oracle ODBC Driver</span></span>

<span data-ttu-id="f251e-318">Le pilote ODBC Microsoft SQL Server Oracle prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="f251e-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="f251e-319">Tables</span><span class="sxs-lookup"><span data-stu-id="f251e-319">Tables</span></span>

- <span data-ttu-id="f251e-320">Colonnes</span><span class="sxs-lookup"><span data-stu-id="f251e-320">Columns</span></span>

- <span data-ttu-id="f251e-321">Procédures</span><span class="sxs-lookup"><span data-stu-id="f251e-321">Procedures</span></span>

- <span data-ttu-id="f251e-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f251e-322">ProcedureColumns</span></span>

- <span data-ttu-id="f251e-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f251e-323">ProcedureParameters</span></span>

- <span data-ttu-id="f251e-324">Affichages</span><span class="sxs-lookup"><span data-stu-id="f251e-324">Views</span></span>

- <span data-ttu-id="f251e-325">Index</span><span class="sxs-lookup"><span data-stu-id="f251e-325">Indexes</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="f251e-326">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="f251e-326">Tables and Views</span></span>

|<span data-ttu-id="f251e-327">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-327">ColumnName</span></span>|<span data-ttu-id="f251e-328">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-328">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f251e-330">String</span><span class="sxs-lookup"><span data-stu-id="f251e-330">String</span></span>|
|<span data-ttu-id="f251e-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f251e-331">TABLE_OWNER</span></span>|<span data-ttu-id="f251e-332">String</span><span class="sxs-lookup"><span data-stu-id="f251e-332">String</span></span>|
|<span data-ttu-id="f251e-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-333">TABLE_NAME</span></span>|<span data-ttu-id="f251e-334">String</span><span class="sxs-lookup"><span data-stu-id="f251e-334">String</span></span>|
|<span data-ttu-id="f251e-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-335">TABLE_TYPE</span></span>|<span data-ttu-id="f251e-336">String</span><span class="sxs-lookup"><span data-stu-id="f251e-336">String</span></span>|
|<span data-ttu-id="f251e-337">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-337">REMARKS</span></span>|<span data-ttu-id="f251e-338">String</span><span class="sxs-lookup"><span data-stu-id="f251e-338">String</span></span>|

### <a name="columns"></a><span data-ttu-id="f251e-339">Colonnes</span><span class="sxs-lookup"><span data-stu-id="f251e-339">Columns</span></span>

|<span data-ttu-id="f251e-340">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-340">ColumnName</span></span>|<span data-ttu-id="f251e-341">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-341">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f251e-343">String</span><span class="sxs-lookup"><span data-stu-id="f251e-343">String</span></span>|
|<span data-ttu-id="f251e-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f251e-344">TABLE_OWNER</span></span>|<span data-ttu-id="f251e-345">String</span><span class="sxs-lookup"><span data-stu-id="f251e-345">String</span></span>|
|<span data-ttu-id="f251e-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-346">TABLE_NAME</span></span>|<span data-ttu-id="f251e-347">String</span><span class="sxs-lookup"><span data-stu-id="f251e-347">String</span></span>|
|<span data-ttu-id="f251e-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-348">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-349">String</span><span class="sxs-lookup"><span data-stu-id="f251e-349">String</span></span>|
|<span data-ttu-id="f251e-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-350">DATA_TYPE</span></span>|<span data-ttu-id="f251e-351">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-351">Int16</span></span>|
|<span data-ttu-id="f251e-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-352">TYPE_NAME</span></span>|<span data-ttu-id="f251e-353">String</span><span class="sxs-lookup"><span data-stu-id="f251e-353">String</span></span>|
|<span data-ttu-id="f251e-354">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f251e-354">PRECISION</span></span>|<span data-ttu-id="f251e-355">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-355">Int32</span></span>|
|<span data-ttu-id="f251e-356">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-356">LENGTH</span></span>|<span data-ttu-id="f251e-357">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-357">Int32</span></span>|
|<span data-ttu-id="f251e-358">SCALE</span><span class="sxs-lookup"><span data-stu-id="f251e-358">SCALE</span></span>|<span data-ttu-id="f251e-359">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-359">Int16</span></span>|
|<span data-ttu-id="f251e-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="f251e-360">RADIX</span></span>|<span data-ttu-id="f251e-361">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-361">Int16</span></span>|
|<span data-ttu-id="f251e-362">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-362">NULLABLE</span></span>|<span data-ttu-id="f251e-363">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-363">Int16</span></span>|
|<span data-ttu-id="f251e-364">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-364">REMARKS</span></span>|<span data-ttu-id="f251e-365">String</span><span class="sxs-lookup"><span data-stu-id="f251e-365">String</span></span>|
|<span data-ttu-id="f251e-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-367">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-367">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="f251e-368">Procédures</span><span class="sxs-lookup"><span data-stu-id="f251e-368">Procedures</span></span>

|<span data-ttu-id="f251e-369">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-369">ColumnName</span></span>|<span data-ttu-id="f251e-370">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-370">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f251e-372">String</span><span class="sxs-lookup"><span data-stu-id="f251e-372">String</span></span>|
|<span data-ttu-id="f251e-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f251e-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f251e-374">String</span><span class="sxs-lookup"><span data-stu-id="f251e-374">String</span></span>|
|<span data-ttu-id="f251e-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="f251e-376">String</span><span class="sxs-lookup"><span data-stu-id="f251e-376">String</span></span>|
|<span data-ttu-id="f251e-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f251e-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f251e-378">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-378">Int16</span></span>|
|<span data-ttu-id="f251e-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f251e-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f251e-380">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-380">Int16</span></span>|
|<span data-ttu-id="f251e-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f251e-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f251e-382">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-382">Int16</span></span>|
|<span data-ttu-id="f251e-383">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-383">REMARKS</span></span>|<span data-ttu-id="f251e-384">String</span><span class="sxs-lookup"><span data-stu-id="f251e-384">String</span></span>|
|<span data-ttu-id="f251e-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f251e-386">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-386">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="f251e-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f251e-387">ProcedureColumns</span></span>

|<span data-ttu-id="f251e-388">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-388">ColumnName</span></span>|<span data-ttu-id="f251e-389">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-389">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f251e-391">String</span><span class="sxs-lookup"><span data-stu-id="f251e-391">String</span></span>|
|<span data-ttu-id="f251e-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f251e-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f251e-393">String</span><span class="sxs-lookup"><span data-stu-id="f251e-393">String</span></span>|
|<span data-ttu-id="f251e-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="f251e-395">String</span><span class="sxs-lookup"><span data-stu-id="f251e-395">String</span></span>|
|<span data-ttu-id="f251e-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-396">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-397">String</span><span class="sxs-lookup"><span data-stu-id="f251e-397">String</span></span>|
|<span data-ttu-id="f251e-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-398">COLUMN_TYPE</span></span>|<span data-ttu-id="f251e-399">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-399">Int16</span></span>|
|<span data-ttu-id="f251e-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-400">DATA_TYPE</span></span>|<span data-ttu-id="f251e-401">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-401">Int16</span></span>|
|<span data-ttu-id="f251e-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-402">TYPE_NAME</span></span>|<span data-ttu-id="f251e-403">String</span><span class="sxs-lookup"><span data-stu-id="f251e-403">String</span></span>|
|<span data-ttu-id="f251e-404">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f251e-404">PRECISION</span></span>|<span data-ttu-id="f251e-405">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-405">Int32</span></span>|
|<span data-ttu-id="f251e-406">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-406">LENGTH</span></span>|<span data-ttu-id="f251e-407">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-407">Int32</span></span>|
|<span data-ttu-id="f251e-408">SCALE</span><span class="sxs-lookup"><span data-stu-id="f251e-408">SCALE</span></span>|<span data-ttu-id="f251e-409">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-409">Int16</span></span>|
|<span data-ttu-id="f251e-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="f251e-410">RADIX</span></span>|<span data-ttu-id="f251e-411">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-411">Int16</span></span>|
|<span data-ttu-id="f251e-412">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-412">NULLABLE</span></span>|<span data-ttu-id="f251e-413">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-413">Int16</span></span>|
|<span data-ttu-id="f251e-414">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-414">REMARKS</span></span>|<span data-ttu-id="f251e-415">String</span><span class="sxs-lookup"><span data-stu-id="f251e-415">String</span></span>|
|<span data-ttu-id="f251e-416">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="f251e-416">OVERLOAD</span></span>|<span data-ttu-id="f251e-417">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-417">Int32</span></span>|
|<span data-ttu-id="f251e-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-419">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-419">Int32</span></span>|

## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="f251e-420">Pilote Microsoft Jet ODBC</span><span class="sxs-lookup"><span data-stu-id="f251e-420">Microsoft Jet ODBC Driver</span></span>

<span data-ttu-id="f251e-421">Le pilote Microsoft Jet ODBC prend en charge les collections de schémas spécifiques suivantes en plus des collections de schémas courantes :</span><span class="sxs-lookup"><span data-stu-id="f251e-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>

- <span data-ttu-id="f251e-422">Tables</span><span class="sxs-lookup"><span data-stu-id="f251e-422">Tables</span></span>

- <span data-ttu-id="f251e-423">Index</span><span class="sxs-lookup"><span data-stu-id="f251e-423">Indexes</span></span>

- <span data-ttu-id="f251e-424">Colonnes</span><span class="sxs-lookup"><span data-stu-id="f251e-424">Columns</span></span>

- <span data-ttu-id="f251e-425">Procédures</span><span class="sxs-lookup"><span data-stu-id="f251e-425">Procedures</span></span>

- <span data-ttu-id="f251e-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f251e-426">ProcedureColumns</span></span>

- <span data-ttu-id="f251e-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f251e-427">ProcedureParameters</span></span>

- <span data-ttu-id="f251e-428">Affichages</span><span class="sxs-lookup"><span data-stu-id="f251e-428">Views</span></span>

### <a name="tables-and-views"></a><span data-ttu-id="f251e-429">Tables et vues</span><span class="sxs-lookup"><span data-stu-id="f251e-429">Tables and Views</span></span>

|<span data-ttu-id="f251e-430">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-430">ColumnName</span></span>|<span data-ttu-id="f251e-431">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-431">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f251e-433">String</span><span class="sxs-lookup"><span data-stu-id="f251e-433">String</span></span>|
|<span data-ttu-id="f251e-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f251e-434">TABLE_OWNER</span></span>|<span data-ttu-id="f251e-435">String</span><span class="sxs-lookup"><span data-stu-id="f251e-435">String</span></span>|
|<span data-ttu-id="f251e-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-436">TABLE_NAME</span></span>|<span data-ttu-id="f251e-437">String</span><span class="sxs-lookup"><span data-stu-id="f251e-437">String</span></span>|
|<span data-ttu-id="f251e-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-438">TABLE_TYPE</span></span>|<span data-ttu-id="f251e-439">String</span><span class="sxs-lookup"><span data-stu-id="f251e-439">String</span></span>|
|<span data-ttu-id="f251e-440">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-440">REMARKS</span></span>|<span data-ttu-id="f251e-441">String</span><span class="sxs-lookup"><span data-stu-id="f251e-441">String</span></span>|

### <a name="columns"></a><span data-ttu-id="f251e-442">Colonnes</span><span class="sxs-lookup"><span data-stu-id="f251e-442">Columns</span></span>

|<span data-ttu-id="f251e-443">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-443">ColumnName</span></span>|<span data-ttu-id="f251e-444">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-444">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="f251e-446">String</span><span class="sxs-lookup"><span data-stu-id="f251e-446">String</span></span>|
|<span data-ttu-id="f251e-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f251e-447">TABLE_OWNER</span></span>|<span data-ttu-id="f251e-448">String</span><span class="sxs-lookup"><span data-stu-id="f251e-448">String</span></span>|
|<span data-ttu-id="f251e-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-449">TABLE_NAME</span></span>|<span data-ttu-id="f251e-450">String</span><span class="sxs-lookup"><span data-stu-id="f251e-450">String</span></span>|
|<span data-ttu-id="f251e-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-451">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-452">String</span><span class="sxs-lookup"><span data-stu-id="f251e-452">String</span></span>|
|<span data-ttu-id="f251e-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-453">DATA_TYPE</span></span>|<span data-ttu-id="f251e-454">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-454">Int16</span></span>|
|<span data-ttu-id="f251e-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-455">TYPE_NAME</span></span>|<span data-ttu-id="f251e-456">String</span><span class="sxs-lookup"><span data-stu-id="f251e-456">String</span></span>|
|<span data-ttu-id="f251e-457">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f251e-457">PRECISION</span></span>|<span data-ttu-id="f251e-458">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-458">Int32</span></span>|
|<span data-ttu-id="f251e-459">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-459">LENGTH</span></span>|<span data-ttu-id="f251e-460">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-460">Int32</span></span>|
|<span data-ttu-id="f251e-461">SCALE</span><span class="sxs-lookup"><span data-stu-id="f251e-461">SCALE</span></span>|<span data-ttu-id="f251e-462">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-462">Int16</span></span>|
|<span data-ttu-id="f251e-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="f251e-463">RADIX</span></span>|<span data-ttu-id="f251e-464">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-464">Int16</span></span>|
|<span data-ttu-id="f251e-465">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-465">NULLABLE</span></span>|<span data-ttu-id="f251e-466">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-466">Int16</span></span>|
|<span data-ttu-id="f251e-467">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-467">REMARKS</span></span>|<span data-ttu-id="f251e-468">String</span><span class="sxs-lookup"><span data-stu-id="f251e-468">String</span></span>|
|<span data-ttu-id="f251e-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-470">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-470">Int32</span></span>|

### <a name="procedures"></a><span data-ttu-id="f251e-471">Procédures</span><span class="sxs-lookup"><span data-stu-id="f251e-471">Procedures</span></span>

|<span data-ttu-id="f251e-472">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-472">ColumnName</span></span>|<span data-ttu-id="f251e-473">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-473">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f251e-475">String</span><span class="sxs-lookup"><span data-stu-id="f251e-475">String</span></span>|
|<span data-ttu-id="f251e-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f251e-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f251e-477">String</span><span class="sxs-lookup"><span data-stu-id="f251e-477">String</span></span>|
|<span data-ttu-id="f251e-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="f251e-479">String</span><span class="sxs-lookup"><span data-stu-id="f251e-479">String</span></span>|
|<span data-ttu-id="f251e-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f251e-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="f251e-481">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-481">Int16</span></span>|
|<span data-ttu-id="f251e-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="f251e-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="f251e-483">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-483">Int16</span></span>|
|<span data-ttu-id="f251e-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="f251e-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="f251e-485">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-485">Int16</span></span>|
|<span data-ttu-id="f251e-486">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-486">REMARKS</span></span>|<span data-ttu-id="f251e-487">String</span><span class="sxs-lookup"><span data-stu-id="f251e-487">String</span></span>|
|<span data-ttu-id="f251e-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="f251e-489">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-489">Int16</span></span>|

### <a name="procedurecolumns"></a><span data-ttu-id="f251e-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="f251e-490">ProcedureColumns</span></span>

|<span data-ttu-id="f251e-491">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-491">ColumnName</span></span>|<span data-ttu-id="f251e-492">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-492">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="f251e-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="f251e-494">String</span><span class="sxs-lookup"><span data-stu-id="f251e-494">String</span></span>|
|<span data-ttu-id="f251e-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="f251e-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="f251e-496">String</span><span class="sxs-lookup"><span data-stu-id="f251e-496">String</span></span>|
|<span data-ttu-id="f251e-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="f251e-498">String</span><span class="sxs-lookup"><span data-stu-id="f251e-498">String</span></span>|
|<span data-ttu-id="f251e-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-499">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-500">String</span><span class="sxs-lookup"><span data-stu-id="f251e-500">String</span></span>|
|<span data-ttu-id="f251e-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-501">COLUMN_TYPE</span></span>|<span data-ttu-id="f251e-502">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-502">Int16</span></span>|
|<span data-ttu-id="f251e-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-503">DATA_TYPE</span></span>|<span data-ttu-id="f251e-504">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-504">Int16</span></span>|
|<span data-ttu-id="f251e-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-505">TYPE_NAME</span></span>|<span data-ttu-id="f251e-506">String</span><span class="sxs-lookup"><span data-stu-id="f251e-506">String</span></span>|
|<span data-ttu-id="f251e-507">PRECISION</span><span class="sxs-lookup"><span data-stu-id="f251e-507">PRECISION</span></span>|<span data-ttu-id="f251e-508">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-508">Int32</span></span>|
|<span data-ttu-id="f251e-509">LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-509">LENGTH</span></span>|<span data-ttu-id="f251e-510">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-510">Int32</span></span>|
|<span data-ttu-id="f251e-511">SCALE</span><span class="sxs-lookup"><span data-stu-id="f251e-511">SCALE</span></span>|<span data-ttu-id="f251e-512">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-512">Int16</span></span>|
|<span data-ttu-id="f251e-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="f251e-513">RADIX</span></span>|<span data-ttu-id="f251e-514">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-514">Int16</span></span>|
|<span data-ttu-id="f251e-515">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-515">NULLABLE</span></span>|<span data-ttu-id="f251e-516">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-516">Int16</span></span>|
|<span data-ttu-id="f251e-517">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-517">REMARKS</span></span>|<span data-ttu-id="f251e-518">String</span><span class="sxs-lookup"><span data-stu-id="f251e-518">String</span></span>|
|<span data-ttu-id="f251e-519">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="f251e-519">OVERLOAD</span></span>|<span data-ttu-id="f251e-520">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-520">Int32</span></span>|
|<span data-ttu-id="f251e-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-522">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-522">Int32</span></span>|

### <a name="procedureparameters"></a><span data-ttu-id="f251e-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="f251e-523">ProcedureParameters</span></span>

|<span data-ttu-id="f251e-524">ColumnName</span><span class="sxs-lookup"><span data-stu-id="f251e-524">ColumnName</span></span>|<span data-ttu-id="f251e-525">Type de données</span><span class="sxs-lookup"><span data-stu-id="f251e-525">DataType</span></span>|
|----------------|--------------|
|<span data-ttu-id="f251e-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="f251e-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="f251e-527">String</span><span class="sxs-lookup"><span data-stu-id="f251e-527">String</span></span>|
|<span data-ttu-id="f251e-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="f251e-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="f251e-529">String</span><span class="sxs-lookup"><span data-stu-id="f251e-529">String</span></span>|
|<span data-ttu-id="f251e-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="f251e-531">String</span><span class="sxs-lookup"><span data-stu-id="f251e-531">String</span></span>|
|<span data-ttu-id="f251e-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-532">COLUMN_NAME</span></span>|<span data-ttu-id="f251e-533">String</span><span class="sxs-lookup"><span data-stu-id="f251e-533">String</span></span>|
|<span data-ttu-id="f251e-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-534">COLUMN_TYPE</span></span>|<span data-ttu-id="f251e-535">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-535">Int16</span></span>|
|<span data-ttu-id="f251e-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-536">DATA_TYPE</span></span>|<span data-ttu-id="f251e-537">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-537">Int16</span></span>|
|<span data-ttu-id="f251e-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="f251e-538">TYPE_NAME</span></span>|<span data-ttu-id="f251e-539">String</span><span class="sxs-lookup"><span data-stu-id="f251e-539">String</span></span>|
|<span data-ttu-id="f251e-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="f251e-540">COLUMN_SIZE</span></span>|<span data-ttu-id="f251e-541">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-541">Int32</span></span>|
|<span data-ttu-id="f251e-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="f251e-543">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-543">Int32</span></span>|
|<span data-ttu-id="f251e-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="f251e-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="f251e-545">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-545">Int16</span></span>|
|<span data-ttu-id="f251e-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="f251e-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="f251e-547">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-547">Int16</span></span>|
|<span data-ttu-id="f251e-548">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-548">NULLABLE</span></span>|<span data-ttu-id="f251e-549">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-549">Int16</span></span>|
|<span data-ttu-id="f251e-550">REMARKS</span><span class="sxs-lookup"><span data-stu-id="f251e-550">REMARKS</span></span>|<span data-ttu-id="f251e-551">String</span><span class="sxs-lookup"><span data-stu-id="f251e-551">String</span></span>|
|<span data-ttu-id="f251e-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="f251e-552">COLUMN_DEF</span></span>|<span data-ttu-id="f251e-553">String</span><span class="sxs-lookup"><span data-stu-id="f251e-553">String</span></span>|
|<span data-ttu-id="f251e-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="f251e-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="f251e-555">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-555">Int16</span></span>|
|<span data-ttu-id="f251e-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="f251e-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="f251e-557">Int16</span><span class="sxs-lookup"><span data-stu-id="f251e-557">Int16</span></span>|
|<span data-ttu-id="f251e-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="f251e-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="f251e-559">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-559">Int32</span></span>|
|<span data-ttu-id="f251e-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="f251e-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="f251e-561">Int32</span><span class="sxs-lookup"><span data-stu-id="f251e-561">Int32</span></span>|
|<span data-ttu-id="f251e-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="f251e-562">IS_NULLABLE</span></span>|<span data-ttu-id="f251e-563">String</span><span class="sxs-lookup"><span data-stu-id="f251e-563">String</span></span>|

## <a name="see-also"></a><span data-ttu-id="f251e-564">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f251e-564">See also</span></span>

- [<span data-ttu-id="f251e-565">Vue d’ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="f251e-565">ADO.NET Overview</span></span>](ado-net-overview.md)
