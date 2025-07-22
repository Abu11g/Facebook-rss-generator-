# Facebook-rss-generator-
import React, { useState } from "react";

export default function FacebookRssGenerator() { const [title, setTitle] = useState(""); const [link, setLink] = useState(""); const [description, setDescription] = useState(""); const [pubDate, setPubDate] = useState(""); const [rssItem, setRssItem] = useState("");

const generateRssItem = (e) => { e.preventDefault();

const rss = `

<item>
  <title>${title}</title>
  <link>${link}</link>
  <description>${description}</description>
  <pubDate>${pubDate}</pubDate>
  <guid>${link}</guid>
</item>`.trim();setRssItem(rss);

};

return ( <div className="p-4 max-w-2xl mx-auto"> <h1 className="text-2xl font-bold mb-4">📢 Facebook to RSS Generator</h1> <form onSubmit={generateRssItem} className="space-y-4"> <div> <label className="block text-sm font-medium">Post Title</label> <input type="text" value={title} onChange={(e) => setTitle(e.target.value)} className="w-full border rounded p-2" required /> </div>

<div>
      <label className="block text-sm font-medium">Post URL (Facebook link)</label>
      <input
        type="url"
        value={link}
        onChange={(e) => setLink(e.target.value)}
        className="w-full border rounded p-2"
        required
      />
    </div>

    <div>
      <label className="block text-sm font-medium">Short Description</label>
      <textarea
        value={description}
        onChange={(e) => setDescription(e.target.value)}
        className="w-full border rounded p-2"
        rows="3"
        required
      ></textarea>
    </div>

    <div>
      <label className="block text-sm font-medium">Publish Date</label>
      <input
        type="text"
        placeholder="Mon, 22 Jul 2025 12:00:00 GMT"
        value={pubDate}
        onChange={(e) => setPubDate(e.target.value)}
        className="w-full border rounded p-2"
        required
      />
    </div>

    <button
      type="submit"
      className="bg-blue-600 text-white px-4 py-2 rounded hover:bg-blue-700"
    >
      Generate RSS Item
    </button>
  </form>

  {rssItem && (
    <div className="mt-6">
      <h2 className="text-xl font-semibold mb-2">Generated RSS:</h2>
      <pre className="bg-gray-100 p-4 rounded text-sm overflow-x-auto">
        {rssItem}
      </pre>
    </div>
  )}
</div>

); }

