This is a set of LLVM Passes that I wrote for practice.

Testing at own risk.

Git it:
++++++++++++
git clone into $(LLVM_DIR)/llvm/lib/Transforms/

Don't forget to add the new pass' directory to $(LLVM_DIR)/llvm/lib/Transforms/CMakeLists.txt
Alternatively, runi

 echo 'sudirectory(dennis)" >> ../CMakeLists.txt

Build it:
++++++++++++
Go to your LLVM source directory

cd $(LLVM_DIR)/llvm/i

Create a target folder

mkdir build
cd build

Configure and make using cmake
cmake ../
cmake --build .

Use it:
+++++++++++ 
Compile a test file using clang. Emit LLVM IR code, because that's what the Pass works on
clang -o0 -S -emit-llvm test.c -o test.ll

Specify to run the correct ./opt file and choose the LLVM Pass
$(LLVM_DIR)/llvm/bin/opt -load $(LLVM_DIR)/llvm/build/lib/LLVMDennis.dylib --dennis test.ll
