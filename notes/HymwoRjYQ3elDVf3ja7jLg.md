raise ur hack
<pre>
   

import React, { useState, useEffect, useRef } from "react";
import {
  Search,
  Code,
  Users,
  ChevronDown,
  ChevronUp,
  ExternalLink,
  Copy,
  X,
  Filter,
  Share2,
  Check,
} from "lucide-react";

const DevAINewsGenerator = () => {
  [topic, setTopic] = useState("");
  const [isGenerating, setIsGenerating] = useState(false);
  const [newsItems, setNewsItems] = useState([]);
  const [expandedItems, setExpandedItems] = useState(new Set());
  const [selectedModal, setSelectedModal] = useState(null);
  const [searchFilter, setSearchFilter] = useState("");
  const [showFilters, setShowFilters] = useState(false);
  const [categoryFilter, setCategoryFilter] = useState([]);
  const [showCategoryDropdown, setShowCategoryDropdown] = useState(false);
  const [copyMessage, setCopyMessage] = useState("");
  const [copiedStates, setCopiedStates] = useState({}); // Track copied states for each item
  const [modalCopied, setModalCopied] = useState(false); // Track copied state for modal
  const dropdownRef = useRef(null);

  // Mock data for news generation
  const mockNewsData = [
    {
      id: 1,
      title: "OpenAI Releases GPT-4 Preview for Developers",
      summary:
        "OpenAI unveils a preview of GPT-4, accessible via relevant content.",
      insight: "Test the model's capabilities with early access.",
      category: "AI Models",
      sourceUrl:
        "https://edition.cnn.com/2024/03/14/tech/openai-gpt4-preview-developers/index.html",
      code: `// GPT-4 API Example
const response = await openai.chat.completions.create({
  model: "gpt-4-preview",
  messages: [
    { role: "user", content: "Hello, GPT-4!" }
  ]
});`,
      fullContent:
        "OpenAI has released an early preview of GPT-4, offering developers unprecedented access to advanced language model capabilities. This preview version includes enhanced reasoning, better code generation, and improved multimodal understanding. Developers can now experiment with the model through the OpenAI API, providing valuable feedback for the final release.",
    },
    {
      id: 2,
      title: "DeepMind Unveils AlphaTensor for Faster Matrix Multiplication",
      summary: "DeepMind optimizes matrix multiplication optimization.",
      insight: "Explore improvements in computational efficiency.",
      category: "Research",
      sourceUrl:
        "https://edition.cnn.com/2024/03/15/tech/deepmind-alphatensor-matrix/index.html",
      code: `# AlphaTensor-inspired optimization
import numpy as np

def optimized_matmul(A, B):
    # Simplified efficient multiplication
    return np.dot(A, B)`,
      fullContent:
        "DeepMind's AlphaTensor represents a breakthrough in mathematical optimization, discovering new algorithms for matrix multiplication that outperform traditional methods. This AI system has found more efficient ways to multiply matrices, potentially speeding up countless computational tasks across machine learning and scientific computing.",
    },
    {
      id: 3,
      title: "GitHub Copilot Teams Update Supports Collaborative Development",
      summary: "Utilize Copilot in team-based development workflow.",
      insight: "Enhance team productivity with AI-assisted coding.",
      category: "Tools",
      sourceUrl:
        "https://edition.cnn.com/2024/03/16/tech/github-copilot-teams-update/index.html",
      code: `// Copilot Team Configuration
const teamConfig = {
  members: ['dev1', 'dev2', 'dev3'],
  sharedContext: true,
  codeStyle: 'typescript'
};`,
      fullContent:
        "GitHub has announced major updates to Copilot for Teams, introducing collaborative features that allow development teams to share context and coding patterns. The new update includes team-wide code style consistency, shared prompt libraries, and enhanced security features for enterprise environments.",
    },
    {
      id: 4,
      title: "Meta Launches Code Llama 2 for Advanced Programming Tasks",
      summary: "Meta's latest language model specialized for code generation.",
      insight: "Leverage state-of-the-art code completion and generation.",
      category: "AI Models",
      sourceUrl:
        "https://edition.cnn.com/2024/03/17/tech/meta-code-llama-2-programming/index.html",
      code: `// Code Llama 2 API Usage
const codeLlama = new CodeLlama2({
  model: "codellama-34b-instruct",
  temperature: 0.1
});

const result = await codeLlama.generate({
  prompt: "Create a React component for user authentication"
});`,
      fullContent:
        "Meta has released Code Llama 2, an enhanced version of their code-specialized language model. This new iteration offers improved accuracy in code generation, better understanding of programming contexts, and support for more programming languages. The model excels at complex programming tasks and can generate production-ready code snippets.",
    },
    {
      id: 5,
      title: "Anthropic Enhances Claude for Ethical AI Systems",
      summary: "Enhancements focus on safety and robustness.",
      insight: "Explore improvements in ethical AI development.",
      category: "Ethics",
      sourceUrl:
        "https://edition.cnn.com/2024/03/18/tech/anthropic-claude-ethical-ai/index.html",
      code: `// Claude Safety Configuration
const claude = new Claude({
  safetyLevel: 'high',
  ethicalGuidelines: true,
  harmfulnessFilter: 'strict'
});`,
      fullContent:
        "Anthropic has introduced significant improvements to Claude, focusing on safety, alignment, and ethical considerations. The updates include better refusal mechanisms for harmful requests, improved factual accuracy, and enhanced reasoning capabilities while maintaining strong safety guardrails.",
    },
    {
      id: 6,
      title: "Vercel Introduces AI-Powered Frontend Optimization",
      summary: "Automatic performance optimization using machine learning.",
      insight: "Boost web application performance with AI insights.",
      category: "Performance",
      sourceUrl:
        "https://edition.cnn.com/2024/03/19/tech/vercel-ai-frontend-optimization/index.html",
      code: `// Vercel AI Optimization
export default function MyApp() {
  return (
    <div className="optimized-by-ai">
      <h1>Auto-optimized content</h1>
    </div>
  );
}`,
      fullContent:
        "Vercel has launched an AI-powered optimization system that automatically improves frontend performance. The system analyzes user behavior, identifies bottlenecks, and applies optimizations in real-time, resulting in faster load times and better user experiences.",
    },
  ];

  const categories = [
    "AI Models",
    "Research",
    "Tools",
    "Ethics",
    "Performance",
  ];

  // Handle clicks outside dropdown to close it
  useEffect(() => {
    const handleClickOutside = (event) => {
      if (dropdownRef.current && !dropdownRef.current.contains(event.target)) {
        setShowCategoryDropdown(false);
      }
    };

    document.addEventListener("mousedown", handleClickOutside);
    return () => {
      document.removeEventListener("mousedown", handleClickOutside);
    };
  }, []);

  const handleGenerate = async () => {
    if (!topic.trim()) return;

    setIsGenerating(true);
    setNewsItems([]);
    // Reset all copied states when generating new content
    setCopiedStates({});

    // Simulate API call delay
    await new Promise((resolve) => setTimeout(resolve, 2000));

    // Filter mock data based on topic or return random selection
    const filteredNews = mockNewsData.filter(
      (item) =>
        item.title.toLowerCase().includes(topic.toLowerCase()) ||
        item.summary.toLowerCase().includes(topic.toLowerCase()) ||
        item.category.toLowerCase().includes(topic.toLowerCase())
    );

    const newsToShow =
      filteredNews.length > 0 ? filteredNews : mockNewsData.slice(0, 4);
    setNewsItems(newsToShow);
    setIsGenerating(false);
  };

  const toggleExpanded = (id) => {
    const newExpanded = new Set(expandedItems);
    if (newExpanded.has(id)) {
      newExpanded.delete(id);
    } else {
      newExpanded.add(id);
    }
    setExpandedItems(newExpanded);

    // Reset copied state when toggling the expanded view
    setCopiedStates((prev) => ({
      ...prev,
      [id]: false,
    }));
  };

  const openModal = (item) => {
    setSelectedModal(item);
    setModalCopied(false); // Reset modal copied state when opening
  };

  const closeModal = () => {
    setSelectedModal(null);
    setModalCopied(false); // Reset modal copied state when closing
  };

  const copyCode = (code, itemId = null) => {
    navigator.clipboard.writeText(code);
    setCopyMessage("Code copied ✅");
    setTimeout(() => setCopyMessage(""), 3000);

    if (itemId) {
      // Update copied state for specific item
      setCopiedStates((prev) => ({
        ...prev,
        [itemId]: true,
      }));
      // Reset after 2 seconds
      setTimeout(() => {
        setCopiedStates((prev) => ({
          ...prev,
          [itemId]: false,
        }));
      }, 2000);
    } else {
      // Modal copy button
      setModalCopied(true);
      setTimeout(() => setModalCopied(false), 2000);
    }
  };

  const handleCategoryToggle = (category) => {
    setCategoryFilter((prev) =>
      prev.includes(category)
        ? prev.filter((c) => c !== category)
        : [...prev, category]
    );
    // Keep dropdown open for multiple selections
  };

  const clearAllCategories = () => {
    setCategoryFilter([]);
    setShowCategoryDropdown(false);
  };

  const removeCategoryFilter = (category) => {
    setCategoryFilter((prev) => prev.filter((c) => c !== category));
  };

  const shareNewsItem = (item) => {
    // Always copy current webpage URL
    const currentUrl = window.location.href;
    navigator.clipboard.writeText(currentUrl);
    setCopyMessage("Link shared! 📋");
    setTimeout(() => setCopyMessage(""), 3000);
  };

  const filteredNews = newsItems.filter((item) => {
    const matchesSearch =
      item.title.toLowerCase().includes(searchFilter.toLowerCase()) ||
      item.summary.toLowerCase().includes(searchFilter.toLowerCase());
    const matchesCategory =
      categoryFilter.length === 0 || categoryFilter.includes(item.category);
    return matchesSearch && matchesCategory;
  });

  return (
    <div className="min-h-screen bg-gradient-to-br from-slate-900 via-purple-900 to-slate-900">
      {/* Copy Message */}
      {copyMessage && (
        <div className="fixed top-4 right-4 bg-green-500/20 backdrop-blur-sm border border-green-500/30 text-green-300 px-4 py-2 rounded-lg z-50 animate-in slide-in-from-top-2 duration-300">
          {copyMessage}
        </div>
      )}

      {/* Header */}
      <div className="relative overflow-hidden">
        <div className="absolute inset-0 bg-gradient-to-r from-blue-600/20 to-purple-600/20 blur-3xl"></div>
        <div className="relative px-6 py-16 text-center">
          <h1 className="text-5xl font-bold text-white mb-4 bg-gradient-to-r from-blue-400 to-purple-400 bg-clip-text text-transparent">
            Developer AI News Generator
          </h1>
          <p className="text-xl text-slate-300 mb-8">
            Generate concise tech news summaries with code snippets
          </p>

          {/* Search Input */}
          <div className="max-w-2xl mx-auto relative">
            <input
              type="text"
              placeholder="Enter a topic..."
              value={topic}
              onChange={(e) => setTopic(e.target.value)}
              className="w-full px-6 py-4 bg-white/10 backdrop-blur-sm border border-white/20 rounded-2xl text-white placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500/50 focus:border-transparent transition-all duration-300"
              onKeyPress={(e) => e.key === "Enter" && handleGenerate()}
            />
            <button
              onClick={handleGenerate}
              disabled={isGenerating || !topic.trim()}
              className="absolute right-2 top-2 px-8 py-2 bg-gradient-to-r from-blue-500 to-purple-500 text-white rounded-xl hover:from-blue-600 hover:to-purple-600 disabled:opacity-50 disabled:cursor-not-allowed transition-all duration-300 transform hover:scale-105"
            >
              {isGenerating ? "Generating..." : "Generate"}
            </button>
          </div>
        </div>
      </div>

      {/* Agents Section */}
      <div className="px-6 py-12">
        <div className="max-w-6xl mx-auto grid md:grid-cols-2 gap-8">
          <div className="bg-white/10 backdrop-blur-sm rounded-2xl p-8 border border-white/20 hover:bg-white/15 transition-all duration-300 group">
            <div className="flex items-center mb-4">
              <Search className="w-8 h-8 text-blue-400 mr-4 group-hover:scale-110 transition-transform duration-300" />
              <h3 className="text-2xl font-bold text-white">
                Researcher Agent
              </h3>
            </div>
            <p className="text-slate-300 leading-relaxed">
              Scans official AI blogs and developer hubs for relevant content,
              analyzing trends and extracting key insights from the latest
              developments.
            </p>
          </div>

          <div className="bg-white/10 backdrop-blur-sm rounded-2xl p-8 border border-white/20 hover:bg-white/15 transition-all duration-300 group">
            <div className="flex items-center mb-4">
              <Code className="w-8 h-8 text-purple-400 mr-4 group-hover:scale-110 transition-transform duration-300" />
              <h3 className="text-2xl font-bold text-white">Editor Agent</h3>
            </div>
            <p className="text-slate-300 leading-relaxed">
              Creates actionable summaries and code examples, transforming raw
              information into practical insights for developers.
            </p>
          </div>
        </div>
      </div>

      {/* Loading State */}
      {isGenerating && (
        <div className="px-6 py-12">
          <div className="max-w-4xl mx-auto text-center">
            <div className="inline-block animate-spin rounded-full h-12 w-12 border-b-2 border-blue-400 mb-4"></div>
            <p className="text-slate-300 text-lg">
              Generating AI news summaries...
            </p>
          </div>
        </div>
      )}

      {/* News Results */}
      {newsItems.length > 0 && (
        <div className="px-6 py-12">
          <div className="max-w-6xl mx-auto">
            <div className="flex flex-col md:flex-row justify-between items-center mb-8">
              <h2 className="text-3xl font-bold text-white mb-4 md:mb-0">
                Latest Summaries
              </h2>

              {/* Filters */}
              <div className="flex flex-col sm:flex-row gap-4">
                <div className="relative">
                  <Search className="absolute left-3 top-3 w-5 h-5 text-slate-400" />
                  <input
                    type="text"
                    placeholder="Search summaries..."
                    value={searchFilter}
                    onChange={(e) => setSearchFilter(e.target.value)}
                    className="pl-10 pr-4 py-2 bg-white/10 backdrop-blur-sm border border-white/20 rounded-xl text-white placeholder-slate-400 focus:outline-none focus:ring-2 focus:ring-blue-500/50"
                  />
                </div>

                <div className="relative z-20" ref={dropdownRef}>
                  <div className="flex flex-wrap gap-2 p-2 bg-white/10 backdrop-blur-sm border border-white/20 rounded-xl min-h-[42px] focus-within:ring-2 focus-within:ring-blue-500/50 min-w-[200px]">
                    {categoryFilter.length > 0 && (
                      <div className="flex flex-wrap gap-2">
                        {categoryFilter.map((cat) => (
                          <span
                            key={cat}
                            className="px-2 py-1 bg-blue-500/30 text-blue-300 rounded-lg text-sm flex items-center gap-1 border border-blue-500/30"
                          >
                            {cat}
                            <button
                              onClick={() => removeCategoryFilter(cat)}
                              className="hover:bg-blue-500/50 rounded-full p-0.5 transition-colors"
                            >
                              <X className="w-3 h-3" />
                            </button>
                          </span>
                        ))}
                      </div>
                    )}
                    <div className="relative flex-1 min-w-[120px]">
                      <button
                        onClick={() =>
                          setShowCategoryDropdown(!showCategoryDropdown)
                        }
                        className="w-full bg-transparent text-white focus:outline-none text-left flex items-center justify-between px-2 py-1 min-h-[24px]"
                      >
                        <span className="text-slate-300">
                          {categoryFilter.length === 0
                            ? "All Categories"
                            : "Categories"}
                        </span>
                        <Filter className="w-4 h-4 text-slate-400 ml-2 flex-shrink-0" />
                      </button>

                      {showCategoryDropdown && (
                        <div className="absolute top-full left-0 right-0 mt-1 bg-slate-800 border border-white/20 rounded-lg shadow-lg z-30 max-h-48 overflow-y-auto">
                          <button
                            onClick={clearAllCategories}
                            className="w-full text-left px-3 py-2 hover:bg-slate-700 text-white text-sm border-b border-white/10 font-medium"
                          >
                            Clear All
                          </button>
                          {categories.map((cat) => (
                            <button
                              key={cat}
                              onClick={() => handleCategoryToggle(cat)}
                              className={`w-full text-left px-3 py-2 hover:bg-slate-700 text-sm transition-colors flex items-center justify-between ${
                                categoryFilter.includes(cat)
                                  ? "text-blue-300 bg-blue-500/20"
                                  : "text-white"
                              }`}
                            >
                              <span>{cat}</span>
                              {categoryFilter.includes(cat) && (
                                <span className="text-blue-400">✓</span>
                              )}
                            </button>
                          ))}
                        </div>
                      )}
                    </div>
                  </div>
                </div>
              </div>
            </div>

            <div className="grid gap-6 relative z-10">
              {filteredNews.map((item) => (
                <div
                  key={item.id}
                  className="bg-white/10 backdrop-blur-sm rounded-2xl border border-white/20 hover:bg-white/15 transition-all duration-300 group overflow-hidden"
                >
                  <div className="p-6">
                    <div className="flex justify-between items-start mb-4">
                      <div className="flex-1">
                        <div className="flex items-center gap-3 mb-2 flex-wrap">
                          <h3 className="text-xl font-bold text-white hover:text-white transition-colors duration-300 cursor-pointer">
                            {item.title}
                          </h3>
                          <span
                            className="px-3 py-1 bg-gradient-to-r from-blue-500/20 to-purple-500/20 text-blue-300 rounded-full text-sm border border-blue-500/30 cursor-pointer hover:from-blue-500/30 hover:to-purple-500/30 transition-all duration-300"
                            onClick={() => handleCategoryToggle(item.category)}
                          >
                            {item.category}
                          </span>
                        </div>
                        <p className="text-slate-300 mb-3">{item.summary}</p>
                        <div className="flex items-center text-blue-400 mb-4">
                          <Users className="w-4 h-4 mr-2" />
                          <span className="text-sm font-medium">
                            Developer Insight:
                          </span>
                          <span className="text-slate-300 ml-2 text-sm">
                            {item.insight}
                          </span>
                        </div>
                      </div>

                      <div className="flex flex-col gap-2 ml-4">
                        <button
                          onClick={() => toggleExpanded(item.id)}
                          className="p-2 bg-white/10 rounded-lg hover:bg-white/20 transition-all duration-300"
                        >
                          {expandedItems.has(item.id) ? (
                            <ChevronUp className="w-5 h-5 text-white" />
                          ) : (
                            <ChevronDown className="w-5 h-5 text-white" />
                          )}
                        </button>
                        <a
                          href={item.sourceUrl}
                          target="_blank"
                          rel="noopener noreferrer"
                          className="p-2 bg-blue-500/20 rounded-lg hover:bg-blue-500/30 transition-all duration-300 inline-flex items-center justify-center"
                        >
                          <ExternalLink className="w-5 h-5 text-blue-400" />
                        </a>
                        <button
                          onClick={() => shareNewsItem(item)}
                          className="p-2 bg-green-500/20 rounded-lg hover:bg-green-500/30 transition-all duration-300 inline-flex items-center justify-center"
                        >
                          <Share2 className="w-5 h-5 text-green-400" />
                        </button>
                      </div>
                    </div>

                    {expandedItems.has(item.id) && (
                      <div className="mt-4 p-4 bg-black/20 rounded-xl border border-white/10 animate-in slide-in-from-top-2 duration-300">
                        <div className="flex justify-between items-center mb-3">
                          <h4 className="text-white font-semibold">
                            Code Example
                          </h4>
                          <button
                            onClick={() => copyCode(item.code, item.id)}
                            className="flex items-center gap-2 px-3 py-1 bg-white/10 rounded-lg hover:bg-white/20 transition-all duration-300"
                          >
                            {copiedStates[item.id] ? (
                              <>
                                <Check className="w-4 h-4 text-green-400" />
                                <span className="text-sm text-green-400">
                                  Copied
                                </span>
                              </>
                            ) : (
                              <>
                                <Copy className="w-4 h-4 text-slate-400" />
                                <span className="text-sm text-slate-400">
                                  Copy
                                </span>
                              </>
                            )}
                          </button>
                        </div>
                        <pre className="bg-slate-900/50 p-4 rounded-lg overflow-x-auto">
                          <code className="text-sm text-slate-300">
                            {item.code}
                          </code>
                        </pre>
                      </div>
                    )}

                    <div className="flex gap-3 mt-4">
                      <button
                        onClick={() => toggleExpanded(item.id)}
                        className="text-sm text-blue-400 hover:text-blue-300 transition-colors duration-300"
                      >
                        {expandedItems.has(item.id) ? "Hide Code" : "Show Code"}
                      </button>
                      <button
                        onClick={() => openModal(item)}
                        className="text-sm text-purple-400 hover:text-purple-300 transition-colors duration-300"
                      >
                        Read Full Article
                      </button>
                    </div>
                  </div>
                </div>
              ))}
            </div>

            {filteredNews.length === 0 && newsItems.length > 0 && (
              <div className="text-center py-12">
                <p className="text-slate-400 text-lg">
                  No summaries match your search criteria.
                </p>
              </div>
            )}
          </div>
        </div>
      )}

      {/* Modal */}
      {selectedModal && (
        <div className="fixed inset-0 bg-black/50 backdrop-blur-sm flex items-center justify-center p-4 z-50">
          <div className="bg-slate-900 rounded-2xl border border-white/20 max-w-4xl w-full max-h-[85vh] overflow-y-auto">
            <div className="p-6">
              <div className="flex justify-between items-start mb-4">
                <h2 className="text-2xl font-bold text-white hover:text-white transition-colors duration-300 pr-8">
                  {selectedModal.title}
                </h2>
                <div className="flex gap-2">
                  <button
                    onClick={() => shareNewsItem(selectedModal)}
                    className="p-2 bg-green-500/20 rounded-lg hover:bg-green-500/30 transition-all duration-300 flex items-center gap-2"
                    title="Share this news"
                  >
                    <Share2 className="w-5 h-5 text-green-400" />
                  </button>
                  <button
                    onClick={closeModal}
                    className="p-2 hover:bg-white/10 rounded-lg transition-all duration-300"
                  >
                    <X className="w-6 h-6 text-white" />
                  </button>
                </div>
              </div>

              <div className="mb-6">
                <span
                  className="px-3 py-1 bg-gradient-to-r from-blue-500/20 to-purple-500/20 text-blue-300 rounded-full text-sm border border-blue-500/30 cursor-pointer hover:from-blue-500/30 hover:to-purple-500/30 transition-all duration-300"
                  onClick={() => handleCategoryToggle(selectedModal.category)}
                >
                  {selectedModal.category}
                </span>
              </div>

              <div className="prose prose-invert max-w-none">
                <p className="text-slate-300 leading-relaxed mb-6">
                  {selectedModal.fullContent}
                </p>
              </div>

              <div className="mt-6 p-4 bg-black/20 rounded-xl border border-white/10">
                <div className="flex justify-between items-center mb-3">
                  <h4 className="text-white font-semibold">Code Example</h4>
                  <button
                    onClick={() => copyCode(selectedModal.code)}
                    className="flex items-center gap-2 px-3 py-1 bg-white/10 rounded-lg hover:bg-white/20 transition-all duration-300"
                  >
                    {modalCopied ? (
                      <>
                        <Check className="w-4 h-4 text-green-400" />
                        <span className="text-sm text-green-400">Copied</span>
                      </>
                    ) : (
                      <>
                        <Copy className="w-4 h-4 text-slate-400" />
                        <span className="text-sm text-slate-400">Copy</span>
                      </>
                    )}
                  </button>
                </div>
                <pre className="bg-slate-900/50 p-4 rounded-lg overflow-x-auto">
                  <code className="text-sm text-slate-300">
                    {selectedModal.code}
                  </code>
                </pre>
              </div>
            </div>
          </div>
        </div>
      )}
    </div>
  );
};

//export default DevAINewsGenerator;



</pre>