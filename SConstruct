import fnmatch
import os

def RecursiveGlob(pathname, pattern):
    matches = []
    for root, dirnames, filenames in os.walk(pathname):
        for filename in fnmatch.filter(filenames, pattern):
            matchingFile = Glob(os.path.join(root, filename))
            relPath = os.path.join(root, filename)
            #matches.extend((matchingFile, relPath))
            matches.append(relPath)
    return matches

env = Environment(CPPPATH = "#include")

env.VariantDir(variant_dir = "#build/", src_dir = "#src/", duplicate = 0)

srcs = RecursiveGlob("src", "*.cpp")

print(["build/" + f[4:] + "\n" for f in srcs])

var_srcs = ["#build/" + f[4:] for f in srcs]

env.Program("#bin/nQueen", var_srcs)
