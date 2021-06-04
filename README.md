# Binary-Trees
Codes of Binary Tree &amp; BST
        
      VERTICAL TRAVERSAL OF BINARY TREE
      
 vector<int> verticalOrder(Node *root)
    {
        //Your code here
        vector<int> v;
        if(root == NULL)
        return v;
        map<int,vector<int>> m;
        queue<pair<Node*,int>> q;
        q.push({root,0});
        while(!q.empty())
        {
            auto p = q.front();
            Node *curr = p.first;
            int hd = p.second;
            q.pop();
            m[hd].push_back(curr->data);
            if(curr->left)
            q.push({curr->left,hd-1});
            if(curr->right)
            q.push({curr->right,hd+1});
        }
        
        for(auto x:m)
        {
            for(int y:x.second)
            v.push_back(y);
        }
        return v;
    }
