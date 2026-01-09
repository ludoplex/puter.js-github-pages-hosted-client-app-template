# Examples

This document provides practical examples of using Puter.js in your applications.

## Basic Examples

### 1. Hello World with AI

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script src="https://js.puter.com/v2/"></script>
</head>
<body>
    <h1>AI Hello World</h1>
    <button onclick="sayHello()">Say Hello</button>
    <div id="output"></div>

    <script>
        async function sayHello() {
            const response = await puter.ai.chat('Say hello in a creative way!');
            document.getElementById('output').textContent = response;
        }
    </script>
</body>
</html>
```

### 2. File Upload and Storage

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script src="https://js.puter.com/v2/"></script>
</head>
<body>
    <input type="file" id="fileInput">
    <button onclick="uploadFile()">Upload to Cloud</button>
    <button onclick="listFiles()">List Files</button>
    <div id="fileList"></div>

    <script>
        async function uploadFile() {
            const file = document.getElementById('fileInput').files[0];
            if (!file) {
                alert('Please select a file');
                return;
            }
            
            try {
                await puter.fs.write(file.name, file);
                alert(`File "${file.name}" uploaded successfully!`);
                listFiles();
            } catch (error) {
                alert('Error: ' + error.message);
            }
        }

        async function listFiles() {
            try {
                const files = await puter.fs.readdir('/');
                const list = files.map(f => f.name).join(', ');
                document.getElementById('fileList').textContent = 'Files: ' + list;
            } catch (error) {
                alert('Error: ' + error.message);
            }
        }
    </script>
</body>
</html>
```

### 3. Simple Todo App with Key-Value Store

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script src="https://js.puter.com/v2/"></script>
    <style>
        .todo-item { padding: 8px; margin: 4px; background: #f0f0f0; }
        .completed { text-decoration: line-through; opacity: 0.6; }
    </style>
</head>
<body>
    <h1>Todo App</h1>
    <input type="text" id="todoInput" placeholder="New todo...">
    <button onclick="addTodo()">Add</button>
    <div id="todoList"></div>

    <script>
        let todos = [];

        async function loadTodos() {
            try {
                const saved = await puter.kv.get('todos');
                todos = saved ? JSON.parse(saved) : [];
                renderTodos();
            } catch (error) {
                console.error('Error loading todos:', error);
                todos = [];
            }
        }

        async function saveTodos() {
            try {
                await puter.kv.set('todos', JSON.stringify(todos));
            } catch (error) {
                alert('Error saving: ' + error.message);
            }
        }

        async function addTodo() {
            const input = document.getElementById('todoInput');
            if (!input.value.trim()) return;
            
            todos.push({ text: input.value, completed: false, id: Date.now() });
            input.value = '';
            await saveTodos();
            renderTodos();
        }

        async function toggleTodo(id) {
            const todo = todos.find(t => t.id === id);
            if (todo) {
                todo.completed = !todo.completed;
                await saveTodos();
                renderTodos();
            }
        }

        async function deleteTodo(id) {
            todos = todos.filter(t => t.id !== id);
            await saveTodos();
            renderTodos();
        }

        function renderTodos() {
            const list = document.getElementById('todoList');
            list.innerHTML = todos.map(todo => `
                <div class="todo-item ${todo.completed ? 'completed' : ''}">
                    <input type="checkbox" 
                           ${todo.completed ? 'checked' : ''} 
                           onchange="toggleTodo(${todo.id})">
                    <span>${todo.text}</span>
                    <button onclick="deleteTodo(${todo.id})">Delete</button>
                </div>
            `).join('');
        }

        // Load todos on startup
        loadTodos();
    </script>
</body>
</html>
```

### 4. User Authentication Example

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script src="https://js.puter.com/v2/"></script>
</head>
<body>
    <div id="loginArea">
        <button onclick="login()">Sign In</button>
    </div>
    <div id="userArea" style="display:none;">
        <h2>Welcome, <span id="username"></span>!</h2>
        <p>Email: <span id="email"></span></p>
        <button onclick="logout()">Sign Out</button>
    </div>

    <script>
        async function checkAuth() {
            try {
                const user = await puter.auth.getUser();
                if (user) {
                    showUserInfo(user);
                }
            } catch (error) {
                console.log('Not authenticated');
            }
        }

        async function login() {
            try {
                await puter.auth.signIn();
                const user = await puter.auth.getUser();
                showUserInfo(user);
            } catch (error) {
                alert('Login failed: ' + error.message);
            }
        }

        async function logout() {
            try {
                await puter.auth.signOut();
                document.getElementById('loginArea').style.display = 'block';
                document.getElementById('userArea').style.display = 'none';
            } catch (error) {
                alert('Logout failed: ' + error.message);
            }
        }

        function showUserInfo(user) {
            document.getElementById('username').textContent = user.username;
            document.getElementById('email').textContent = user.email || 'Not provided';
            document.getElementById('loginArea').style.display = 'none';
            document.getElementById('userArea').style.display = 'block';
        }

        // Check auth status on load
        checkAuth();
    </script>
</body>
</html>
```

### 5. AI Image Description Tool

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script src="https://js.puter.com/v2/"></script>
</head>
<body>
    <h1>AI Image Describer</h1>
    <input type="file" id="imageInput" accept="image/*">
    <button onclick="describeImage()">Describe Image</button>
    <div>
        <img id="preview" style="max-width: 400px; display: none;">
        <p id="description"></p>
    </div>

    <script>
        document.getElementById('imageInput').addEventListener('change', function(e) {
            const file = e.target.files[0];
            if (file) {
                const reader = new FileReader();
                reader.onload = function(e) {
                    const img = document.getElementById('preview');
                    img.src = e.target.result;
                    img.style.display = 'block';
                };
                reader.readAsDataURL(file);
            }
        });

        async function describeImage() {
            const file = document.getElementById('imageInput').files[0];
            if (!file) {
                alert('Please select an image');
                return;
            }

            document.getElementById('description').textContent = 'Analyzing...';

            try {
                // Upload image to Puter storage
                await puter.fs.write('temp_image.jpg', file);
                
                // Use AI to describe the image
                const description = await puter.ai.chat(
                    'Describe this image in detail.',
                    { image: 'temp_image.jpg' }
                );
                
                document.getElementById('description').textContent = description;
            } catch (error) {
                document.getElementById('description').textContent = 
                    'Error: ' + error.message;
            }
        }
    </script>
</body>
</html>
```

## Advanced Examples

### 6. Real-time Collaborative Notes

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <script src="https://js.puter.com/v2/"></script>
</head>
<body>
    <h1>Collaborative Notes</h1>
    <textarea id="notepad" rows="20" cols="80"></textarea>
    <br>
    <button onclick="saveNote()">Save</button>
    <button onclick="loadNote()">Load</button>

    <script>
        const SYNC_INTERVAL = 5000; // 5 seconds
        let lastSaved = '';

        async function saveNote() {
            const content = document.getElementById('notepad').value;
            try {
                await puter.kv.set('shared_note', content);
                await puter.kv.set('shared_note_time', new Date().toISOString());
                lastSaved = content;
                console.log('Note saved');
            } catch (error) {
                alert('Save failed: ' + error.message);
            }
        }

        async function loadNote() {
            try {
                const content = await puter.kv.get('shared_note');
                const time = await puter.kv.get('shared_note_time');
                if (content) {
                    document.getElementById('notepad').value = content;
                    lastSaved = content;
                    console.log('Note loaded, last updated:', time);
                }
            } catch (error) {
                console.error('Load failed:', error);
            }
        }

        // Auto-save on change
        document.getElementById('notepad').addEventListener('input', function() {
            clearTimeout(this.saveTimeout);
            this.saveTimeout = setTimeout(saveNote, 2000);
        });

        // Auto-sync (check for updates from other users)
        setInterval(async () => {
            try {
                const content = await puter.kv.get('shared_note');
                if (content && content !== lastSaved) {
                    const current = document.getElementById('notepad').value;
                    if (current === lastSaved) {
                        // Only update if user hasn't made changes
                        document.getElementById('notepad').value = content;
                        lastSaved = content;
                        console.log('Note updated from remote');
                    }
                }
            } catch (error) {
                console.error('Sync failed:', error);
            }
        }, SYNC_INTERVAL);

        // Load on startup
        loadNote();
    </script>
</body>
</html>
```

## Tips for Building with Puter.js

1. **Error Handling**: Always wrap Puter.js calls in try-catch blocks
2. **Authentication**: Many features require user authentication
3. **Storage Limits**: Be mindful of storage quotas
4. **Testing**: Test with both authenticated and unauthenticated states
5. **Performance**: Cache data locally when possible
6. **Privacy**: Inform users about data stored in the cloud

## More Resources

- [Puter.js Documentation](https://docs.puter.com/)
- [Puter.js API Reference](https://docs.puter.com/api)
- [Community Examples](https://github.com/HeyPuter/puter/discussions)
