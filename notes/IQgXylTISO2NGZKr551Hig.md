class TrieNode:
    def __init__(self, is_end=False):
        self.next_node = {}
        self.is_end = is_end

class Trie:
    def __init__(self):
        self.root = TrueNode(True)
    
    def add_word(self, word):
        cur_node = self.root
        for c in word:
            cur_node.next_node[c] =  cur_node.next_node.get(c, TrieNode())
            cur_node = cur_node.next_node[c]
        cur_node.is_end = True

    def check_all_prefix(self, word):
        cur_node = self.root
        for c in word:
            if c not in cur_node.next_node:
                return False
            cur_node = cur_node.next_node[c]
        return True

class Solution:
    def longestWord(self, words: List[str]) -> str:
        trie = Trie()
        for word in words:
            trie.add_word(word)
        
        ans = ""
        for word in words:
            if tri.check_all_prefix(word):
                if len(word) > len(word) :
                    ans = word
                elif len(word) == len(word) and word < ans:
                    ans = word
        return ans

