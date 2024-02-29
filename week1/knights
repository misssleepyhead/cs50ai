from logic import *

AKnight = Symbol("A is a Knight")
AKnave = Symbol("A is a Knave")

BKnight = Symbol("B is a Knight")
BKnave = Symbol("B is a Knave")

CKnight = Symbol("C is a Knight")
CKnave = Symbol("C is a Knave")

# Puzzle 0
# A says "I am both a knight and a knave."
# A must be knave since a man can't be both and knight can't lie
knowledge0 = And(
    Not(And(AKnight, AKnave)),
    Or(AKnight, AKnave),
    Implication(Not(And(AKnave, AKnight)),  AKnave),
    Implication(AKnight, Not(And(AKnave, AKnight)))
)

# Puzzle 1
# A says "We are both knaves."
# B says nothing.
# if a is a knave then one of them is not knave,
knowledge1 = And(
    Not(And(AKnave, BKnave)),
    Or(AKnave, AKnight),
    Not(AKnight),
    Or(BKnave, BKnight),
    Implication (AKnave, Not(And(AKnave, BKnave)))

    # Implication (BKnight, Not(And(AKnave, BKnave))),


)

# Puzzle 2
# A says "We are the same kind."
# B says "We are of different kinds."
knowledge2 = And(
    Implication(AKnave, Not(Or(And(AKnave, BKnave), And(AKnight, BKnight)))),
    Implication(AKnight, And(AKnight, BKnight)),
    Not(And(AKnight, AKnave)),
    Not(And(BKnight, BKnave)),
    Implication(AKnave, BKnight),
    Implication(BKnave,Or(And(AKnave, BKnave), And(AKnight, BKnight))),
    Implication(BKnight, Not(And(AKnight, BKnight))),
    Implication(BKnight, Not(And(AKnave, BKnave))),
    Implication(BKnight, AKnave),
    Or(AKnave, AKnight),
    Or(BKnave, BKnight)



)

# Puzzle 3
# A says either "I am a knight." or "I am a knave.", but you don't know which.
# B says "A said 'I am a knave'."
# B says "C is a knave."
# C says "A is a knight."
knowledge3 = And(
    Or(AKnave, AKnight),
    Or(BKnave, BKnight),
    Or(CKnave, CKnight),
    Not(And(AKnight, AKnave)),
    Not(And(BKnight, BKnave)),
    Not(And(CKnight, CKnave)),
    Or(And(AKnight,CKnight), BKnight),
    Or(And(AKnave, CKnave), BKnave),
    Or(Implication(BKnight, And(AKnave, CKnave)),Implication(BKnave, And(AKnight,CKnight))),
    Biconditional(Implication(AKnave, CKnave),Implication(CKnave, AKnave)),
    Biconditional(And(AKnave, CKnave),Not(BKnave)),
    Biconditional(And(AKnight, CKnight), Not(BKnight)),
    Implication(Not(And(AKnight, CKnight)), And(AKnave, CKnave)),
    Implication(AKnight, AKnave) and Implication(AKnave, Not(AKnave))




)


def main():
    symbols = [AKnight, AKnave, BKnight, BKnave, CKnight, CKnave]
    puzzles = [
        ("Puzzle 0", knowledge0),
        ("Puzzle 1", knowledge1),
        ("Puzzle 2", knowledge2),
        ("Puzzle 3", knowledge3)
    ]
    for puzzle, knowledge in puzzles:
        print(puzzle)
        if len(knowledge.conjuncts) == 0:
            print("    Not yet implemented.")
        else:
            for symbol in symbols:
                if model_check(knowledge, symbol):
                    print(f"    {symbol}")


if __name__ == "__main__":
    main()
