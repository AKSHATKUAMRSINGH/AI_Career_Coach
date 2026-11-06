RAG LAB — The Science of Smart Document Processing
An interactive 45-minute self-learning notebook on Text Chunking and Document Processing for RAG.
Files
- RAG_Chunking_Lab.ipynb — interactive lesson and coding playground.
- requirements.txt — dependencies.
- EXPLANATION_VIDEO_SCRIPT.md — suggested 5–7 minute walkthrough.
Run in Google Colab (recommended)
1. Download RAG_Chunking_Lab.ipynb.
2. Open https://colab.research.google.com/.
3. Select File → Upload notebook and upload the notebook.
4. If dependencies are missing, run %pip install ipywidgets scikit-learn.
5. Run cells from top to bottom with Shift+Enter or choose Runtime → Run all.
6. Use the chunking sliders, retrieval controls, challenge, and quiz.
Run locally on Windows
No Docker, WSL, GPU, API key, or paid model is required.
1. Install Python 3.10+ from https://www.python.org/downloads/.
2. Open Command Prompt in the extracted folder.
3. Run:py -m venv .venv
   .venv\\Scripts\\activate
   python -m pip install --upgrade pip
   pip install -r requirements.txt
   jupyter notebook
4. Open RAG_Chunking_Lab.ipynb and run cells in order.
5. If widgets fail in classic Notebook, use JupyterLab or Google Colab.
Dependencies
- ipywidgets — interactive controls.
- scikit-learn — TF-IDF and cosine similarity.
- notebook and ipykernel — local notebook runtime.
45-minute pacing
Section	Time
The problem	4 min
Chunking fundamentals	6 min
Interactive playground	9 min
Document processing	6 min
Retrieval simulator	8 min
Hands-on challenge	7 min
Knowledge check	5 min
Total	45 min


Technical limitations
- The splitter counts words, not model-specific tokens. Production systems should use the relevant tokenizer or structure-aware splitting.
- Retrieval uses TF-IDF lexical similarity, not semantic embeddings. It may miss synonyms and paraphrases.
- The sample corpus is synthetic educational content, not official university policy.
- This is a teaching prototype, not a production ingestion service.
- Production systems should add robust PDF/DOCX parsing, OCR, structure-aware splitting, access-control filtering, versioning, embeddings, a vector store, evaluation, and observability.
- Similarity scores are ranking signals, not proof that a chunk answers a question.
Publish on GitHub
1. Create a public repository named rag-chunking-lab.
2. Put the notebook, README, requirements, and video script in the repository.
3. In Command Prompt/terminal from this folder:git init
   git add .
   git commit -m "Add interactive RAG chunking learning lab"
   git branch -M main
   git remote add origin https://github.com/YOUR_USERNAME/rag-chunking-lab.git
   git push -u origin main
4. Replace YOUR_USERNAME with your GitHub username.
5. Add this badge near the top of README, replacing the username:[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/rag-chunking-lab/blob/main/RAG_Chunking_Lab.ipynb)
6. Test the badge in an incognito window. GitHub's notebook preview is static; run the notebook in Colab/Jupyter for interactive controls.
7. Add your explanation-video link to the README or submission form, as appropriate.
Final quality checklist
- [ ] Notebook opens in Colab.
- [ ] Run all cells in a fresh runtime.
- [ ] Chunking controls update output.
- [ ] Retrieval question and top-k controls update ranked results.
- [ ] Challenge controls run.
- [ ] Quiz scores answers and explains them.
- [ ] No API keys or private data are included.
- [ ] README setup instructions work.
- [ ] Public GitHub repository and Colab badge work.
- [ ] Video demonstrates the artifact and explains design trade-offs.

# array.prototype.flatmap <sup>[![Version Badge][npm-version-svg]][package-url]</sup>

[![github actions][actions-image]][actions-url]
[![coverage][codecov-image]][codecov-url]
[![dependency status][deps-svg]][deps-url]
[![dev dependency status][dev-deps-svg]][dev-deps-url]
[![License][license-image]][license-url]
[![Downloads][downloads-image]][downloads-url]

[![npm badge][npm-badge-png]][package-url]

An ES2019 spec-compliant `Array.prototype.flatMap` shim/polyfill/replacement that works as far down as ES3.

This package implements the [es-shim API](https://github.com/es-shims/api) interface. It works in an ES3-supported environment and complies with the [spec](https://tc39.es/ecma262/#sec-array.prototype.flatmap).

Because `Array.prototype.flatMap` depends on a receiver (the `this` value), the main export takes the array to operate on as the first argument.

## Getting started

```sh
npm install --save array.prototype.flatmap
```

## Usage/Examples

```js
var flatMap = require('array.prototype.flatmap');
var assert = require('assert');

var arr = [1, [2], [], 3];

var results = flatMap(arr, function (x, i) {
	assert.equal(x, arr[i]);
	return x;
});

assert.deepEqual(results, [1, 2, 3]);
```

```js
var flatMap = require('array.prototype.flatmap');
var assert = require('assert');
/* when Array#flatMap is not present */
delete Array.prototype.flatMap;
var shimmedFlatMap = flatMap.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedFlatMap, flatMap.getPolyfill());
assert.deepEqual(arr.flatMap(mapper), flatMap(arr, mapper));
```

```js
var flatMap = require('array.prototype.flatmap');
var assert = require('assert');
/* when Array#flatMap is present */
var shimmedIncludes = flatMap.shim();

var mapper = function (x) { return [x, 1]; };

assert.equal(shimmedIncludes, Array.prototype.flatMap);
assert.deepEqual(arr.flatMap(mapper), flatMap(arr, mapper));
```

## Tests
Simply clone the repo, `npm install`, and run `npm test`

[package-url]: https://npmjs.org/package/array.prototype.flatmap
[npm-version-svg]: https://versionbadg.es/es-shims/Array.prototype.flatMap.svg
[deps-svg]: https://david-dm.org/es-shims/Array.prototype.flatMap.svg
[deps-url]: https://david-dm.org/es-shims/Array.prototype.flatMap
[dev-deps-svg]: https://david-dm.org/es-shims/Array.prototype.flatMap/dev-status.svg
[dev-deps-url]: https://david-dm.org/es-shims/Array.prototype.flatMap#info=devDependencies
[npm-badge-png]: https://nodei.co/npm/array.prototype.flatmap.png?downloads=true&stars=true
[license-image]: https://img.shields.io/npm/l/array.prototype.flatmap.svg
[license-url]: LICENSE
[downloads-image]: https://img.shields.io/npm/dm/array.prototype.flatmap.svg
[downloads-url]: https://npm-stat.com/charts.html?package=array.prototype.flatmap
[codecov-image]: https://codecov.io/gh/es-shims/Array.prototype.flatMap/branch/main/graphs/badge.svg
[codecov-url]: https://app.codecov.io/gh/es-shims/Array.prototype.flatMap/
[actions-image]: https://img.shields.io/endpoint?url=https://github-actions-badge-u3jn4tfpocch.runkit.sh/es-shims/Array.prototype.flatMap
[actions-url]: https://github.com/es-shims/Array.prototype.flatMap/actions
