# GitHub Folder Tree 🌲

**github-folder-tree** is a React custom hook that allows you to fetch and process the contents of a GitHub folder. It retrieves information about the files and subfolders in the specified folder, including their names, file types, download URLs, SHA hashes, sizes, and paths.

## Installation ⬇️

To install `github-folder-tree`, use npm or yarn:

```bash
npm install github-folder-tree

# or

yarn add github-folder-tree
```

## Usage 🛠️

To use `github-folder-tree`, import it into your React component:

```javascript
import {useGitHubFolderTree} from 'github-folder-tree';
```

**repositoryUrl** is the URL of the GitHub repository, and **apiKey** is an optional GitHub API key for authentication.

```jsx
const { repoFiles, error, log, fetchRepositoryContents } = useGitHubFolderTree(repositoryUrl, apiKey);
```

### Example

```javascript
import { useState } from 'react';
import {useGitHubFolderTree} from 'github-folder-tree';

const MyComponent = () => {
  const [repositoryUrl, setRepositoryUrl] = useState('');
  const [apiKey, setApiKey] = useState('');
  const { repoFiles, error, log, fetchRepositoryContents } = useGitHubFolderTree(repositoryUrl, apiKey);

  const handleFetchClick = () => {
    fetchRepositoryContents();
  };

  return (
    <div>
      <input type="text" value={repositoryUrl} onChange={(e) => setRepositoryUrl(e.target.value)} placeholder="Enter GitHub repository URL" />
      <input type="text" value={apiKey} onChange={(e) => setApiKey(e.target.value)} placeholder="Enter GitHub API key (optional)" />
      <button onClick={handleFetchClick}>Fetch Folder Contents</button>
      {error && <div>Error: {error}</div>}
      {log && <div>Log: {log}</div>}
      <table>
        <thead>
          <tr>
            <th>Name</th>
            <th>Type</th>
            <th>Size</th>
          </tr>
        </thead>
        <tbody>
          {repoFiles.map((file) => (
            <tr key={file.download_url}>
              <td>
                <a href={file.download_url}>{file.name}</a>
              </td>
              <td>{file.file_type}</td>
              <td>{file.size}</td>
            </tr>
          ))}
        </tbody>
      </table>
    </div>
  );
};

export default MyComponent;
```

In the above example, **repositoryUrl** is the URL of the GitHub repository, and **apiKey** is an optional GitHub API key for authentication.

To fetch the contents of the root folder of a repository, use the repository URL in the following format:

```bash
https://github.com/{user}/{repo}/tree/{branch}
```

For example:

```bash
https://github.com/sauravhathi/lpu-cse/tree/master
```

To fetch the contents of a specific directory or folder within the repository, append the directory path to the repository URL:

```bash
https://github.com/{user}/{repo}/tree/{branch}/{dir}
```

For example:

```bash
https://github.com/sauravhathi/lpu-cse/tree/master/Subjects
```

Note: Make sure to handle any errors and display them appropriately in your React component.

## Screenshots

#### X-Ratelimit-Limit: 60

<img src="https://github.com/sauravhathi/github-folder-tree/assets/61316762/a0896f79-da0e-43af-a7db-230ad27fa5a4" alt="image" width="500px" height="auto" />

#### API rate limit exceeded
<img src="https://github.com/sauravhathi/github-folder-tree/assets/61316762/6193d3e7-978c-4c66-b54d-26bf582c2cdb" alt="image" width="500px" height="auto" />

#### Using Github API Key(Personal access tokens) - X-Ratelimit-Limit: 5000

<img src="https://github.com/sauravhathi/github-folder-tree/assets/61316762/38c7453c-b920-446e-90e3-9f41bd7df542" alt="image" width="500px" height="auto" />

## Hook Reference 📚

The **useGitHubFolderTree** hook returns the following values:

| Name | Type | Description |
| --- | --- | --- |
| **repoFiles** | **RepoFile[]** | An array of objects representing the files in the GitHub folder. |
| **error** | **string** | An error message if an error occurred during the fetch. |
| **log** | **string** | Log messages for tracking progress and debugging. |
| **fetchRepositoryContents** | **function** | A function that fetches the contents of the specified GitHub folder. |

## Contributing 🤝

Contributions are welcome! If you find any issues or have suggestions for improvements, please open an issue or submit a pull request on the GitHub repository.

When contributing to this project, please ensure that your changes are [well-documented](https://github.com/sauravhathi/github-folder-tree/blob/master/CONTRIBUTING.md) and follow the existing code style and conventions.

## Reporting Issues 🐛

If you encounter any issues with github-folder-tree, please open an issue on the [GitHub Repository](https://github.com/sauravhathi/github-folder-tree/issues/new/choose). Provide detailed information about the problem, including steps to reproduce it, error messages (if applicable), and any other relevant information.

## Acknowledgments 🙏

This package was inspired by the need to easily fetch and process the contents of a GitHub folder in React applications.

## Related Projects 🔗

Here are some related projects that you may find useful:

- [github-repository-downloader](https://github.com/sauravhathi/github-repository-downloader) - GitHub Repository Downloader is a convenient and user-friendly tool that allows you to easily download entire repositories or specific folders from GitHub as a ZIP file. GitHub Repository Downloader makes it easy to get the files you need.

- [GitHub Repository Data Extractor](https://github.com/sauravhathi/GitHub-Repository-Data-Extractor) - This is a simple tool that extracts data from a GitHub repository and formats it into JSON and Markdown. The extracted data is then displayed in JSON and Markdown formats for easy viewing and sharing.

## About the Author 👨‍💻

This package is maintained by [Saurav Hathi](https://github.com/sauravhathi). You can find more of my projects on [GitHub](https://github.com/sauravhathi?tab=repositories).

If you have any questions or need further assistance, feel free to reach out to me.

## License

This project is licensed under the [MIT License](https://github.com/sauravhathi/github-folder-tree/blob/master/LICENSE).
