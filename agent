import csv

def load_tree(path):
    nodes = {}
    with open(path, newline="", encoding="utf-8") as f:
        reader = csv.DictReader(f, delimiter="\t")
        for row in reader:
            nodes[row["id"]] = row
    return nodes

def next_from_decision(node, last_answer):
    rules = node["options"].split(";")
    for rule in rules:
        if ":" not in rule:
            continue
        left, target = rule.split(":", 1)
        vals = left.replace("answer=", "").split("|")
        if last_answer in vals:
            return target
    return None

def run():
    nodes = load_tree("../tree/reflection-tree.tsv")
    current = "START"
    last_answer = ""
    while current:
        node = nodes[current]
        t = node["type"]
        text = node["text"]
        if text:
            print("\n" + text)

        if t == "question":
            options = node["options"].split("|")
            for i, opt in enumerate(options, 1):
                print(f"{i}. {opt}")
            choice = int(input("Choose: "))
            last_answer = options[choice - 1]

            # simple next by parent lookup
            children = [n["id"] for n in nodes.values() if n["parentId"] == current]
            current = children[0] if children else node.get("target") or None

        elif t == "decision":
            current = next_from_decision(node, last_answer)

        elif t in ["start", "reflection", "bridge", "summary"]:
            if node.get("target"):
                current = node["target"]
            else:
                children = [n["id"] for n in nodes.values() if n["parentId"] == current]
                current = children[0] if children else None

        elif t == "end":
            break
        else:
            break

if __name__ == "__main__":
    run()
