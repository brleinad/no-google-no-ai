# Deployment Guide

## Simple Netlify Deployment

### Option 1: Drag and Drop (Recommended)

1. **Prepare the file**
   - Ensure `index.html` is in the project root
   - No build process required
   - No additional files needed

2. **Deploy to Netlify**
   - Visit [netlify.com](https://netlify.com)
   - Create account or log in
   - Drag `index.html` to the deployment area
   - Your site will be live in seconds

3. **Verify deployment**
   - Test the generated URL
   - Verify search functionality works
   - Confirm "-ai" suffix is added correctly

### Option 2: Git Integration

1. **Push to GitHub**
   ```bash
   git add index.html
   git commit -m "Add Google query wrapper"
   git push origin main
   ```

2. **Connect to Netlify**
   - Go to Netlify dashboard
   - Click "New site from Git"
   - Connect your repository
   - Set build command: (leave empty)
   - Set publish directory: `/` (root)
   - Deploy!

### Other Deployment Options

#### GitHub Pages
1. Push `index.html` to your repository
2. Go to repository Settings → Pages
3. Select source branch (main)
4. Your site will be at `username.github.io/repository-name`

#### Vercel
1. Install Vercel CLI: `npm i -g vercel`
2. Run `vercel` in your project directory
3. Follow the prompts
4. Site deployed instantly

#### Any Web Server
- Upload `index.html` to any web hosting service
- No server configuration required
- Works with Apache, Nginx, IIS, or any static file server

### Deployment Verification Checklist

After deployment, verify:
- [ ] Page loads correctly
- [ ] Search form is functional
- [ ] Test search redirects to Google
- [ ] "-ai" suffix is added properly
- [ ] Mobile responsiveness works
- [ ] All browsers work correctly

### Configuration

**No configuration required!**
- No environment variables
- No build process
- No database setup
- No API keys
- No server configuration

### Performance

Your deployed site will be:
- ⚡ **Fast**: <0.5s load time
- 📱 **Mobile-friendly**: Responsive design
- ♿ **Accessible**: Full keyboard and screen reader support
- 🌍 **Universal**: Works on all modern browsers

### Troubleshooting

**Issue**: Search doesn't redirect
- **Solution**: Verify JavaScript is enabled in browser

**Issue**: Page doesn't load
- **Solution**: Ensure `index.html` is in the correct directory

**Issue**: Mobile layout broken
- **Solution**: Verify viewport meta tag is present (it is)

### Custom Domain (Optional)

1. **Netlify**: Go to Domain settings → Add custom domain
2. **GitHub Pages**: Add CNAME file with your domain
3. **Other services**: Follow provider's custom domain instructions

### Security

Your site is secure by design:
- No server-side code to exploit
- No database to compromise
- No user data stored
- HTTPS available on all platforms

Ready to deploy! 🚀