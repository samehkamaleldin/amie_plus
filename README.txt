Utilities to generate predictions using AMIE.

- Sampling predictions

Class: amie.data.eval.PredictionsSampler
Signature: PredictionsSampler <db> <samplesPerRule> <unique> <rules>
Description: Given a set of rules mined by AMIE and the training dataset from which such rules were extracted, this class generates a sample of the predictions and outputs them in the format
rule<TAB>subject<TAB>predicate<TAB>object

Class: amie.data.eval.Evaluator
Signature: Evaluator <inputfile> <trainingDb> <targetDb> [outputManual] [outputAutomatic]
Description: Given a set of predictions in a tab separated format (e.g., output by the PredictionsSampler), the dataset from which the predictions were generated and a target dataset (newer superset of the training dataset), it produces 2 output files whose names must be provided:

outputAutomatic = Predictions evaluated automatically by the program. 
outputManual = Predictions that must be manually evaluated 

Evaluations have the format

rule<TAB>subject<TAB>predicate<TAB>object<TAB>evaluation source<TAB>evaluation result

i.e.,

?x <hasCapital> ?y => ?y <isLocatedIn> ?x	Berlin	<isLocatedIn>	Germany	TargetSource	True

If the prediction violates a functionality constraint, the source is TrainingSource.
TargetSource means the target or newer dataset was used to assess the fact, either because it was found there or it contradicts a functionality constraint. 
ManualEvaluation means the prediction must be verified by means of manual assessment. All these predictions are located in the second output without result.

Class: amie.data.eval.PredictionsMerger
Signature: PredictionsMerger <file1> <file2> [outputfile]
It merges two files with evaluated predictions into a single one, grouping the predictions by the rule that generated them.

Class: amie.data.eval.EvaluationSummarizer
Signature: EvaluationsSummarizer <inputfile> [outputfile]
Given a tab separated file with evaluations, it outputs a summary of hits and misses per rule.

Class: amie.data.eval.RulesHitsEvaluator
Signature: RuleHitsEvaluator <inputfile> <trainingDb> <targetDb>
Given an input file with rules mined from the training datasets, it generates all the predictions made by those rules and evaluates them in the target database, reporting the number of hits.


